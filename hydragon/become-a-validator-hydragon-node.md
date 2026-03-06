# Become a Validator (HydraGon Node)

## Become a Hydra Chain Validator (HydraGon Node)

Hydra Chain validators are permissionless (first-come/first-serve) with up to **50 validator slots**. To become a validator you need **(1) at least 15,000 HYDRA** and **(2) an available slot**.&#x20;

GitHub: <https://github.com/Hydra-Chain/hydragon-node?tab=readme-ov-file>

{% hint style="success" %}
**🚀 Quickstart (5 steps)**

* [ ] [**Install Hydra**](#id-2-download-install-the-hydragon-node) (Executable / Build )
* [ ] [**Generate & secure keys**](#id-3-generate-validator-secrets-keys)
* [ ] [**Node config**](#id-4-configure-the-node)
* [ ] [**Start the node & fully sync**](#id-5-launch-the-node-and-wait-for-sync)
* [ ] [**Register + stake 15,000 HYDRA**](#id-7-register-and-stake-as-validator)
  {% endhint %}

> ⚠️ **Uptime matters:** Inactive validators can be ejected after \~**2 hours** (threshold is \~18,000 blocks depending on block time) and can be **permanently banned** [if not reactivated within \~**72 hours**](#id-9-ejection-ban-recovery-read-this-before-you-need-it)**.**

***

### 1) System requirements

Minimum recommended hardware to run a Hydra validator node:

| Component | Minimum               | Recommended                |
| --------- | --------------------- | -------------------------- |
| CPU       | 4 cores               | 8 cores                    |
| RAM       | 16 GB                 | 32 GB                      |
| Storage   | 200 GB NVMe SSD       | 1 TB NVMe SSD              |
| Network   | High-speed connection | Dedicated server + gigabit |

> 💡 **Hardware tips:** Prefer a secure, stable **Linux server OS** (Debian-like) over desktop OS. Storage requirements grow with the chain over time.

***

### 2) Download / install the HydraGon node

Hydra currently supports **Linux environments** for validators. Choose one option below.

#### Option A: Install via executable (recommended)

1. Download the latest Hydragon Node release from [GitHub Releases](https://github.com/Hydra-Chain/hydragon-node/releases/latest).
2. Unzip it. The extracted folder contains the `hydra` executable.
3. (Optional) Move `hydra` to your system PATH (example):

```bash
sudo mv hydra /usr/local/bin/hydra
sudo chmod +x /usr/local/bin/hydra
hydra version
```

#### Option B: Build from source

**Prerequisite:** Go **>= 1.23.3**

```bash
git clone https://github.com/Hydra-Chain/hydragon-node.git
cd hydragon-node
git checkout prod
make build
```

Notes from the upstream README:

* `CGO_ENABLED=0` is used for a static build (more portable).
* You can cross-compile via `GOOS` / `GOARCH`.&#x20;

***

### 3) Generate validator secrets (keys)

Your validator identity uses **three keys**:

* **ECDSA key** (transactions / account)
* **BLS key** (consensus signing)
* **Networking ECDSA key** (P2P identity)

Hydra recommends storing keys **encrypted locally** and keeping **offline backups**.

#### Create encrypted secrets

```bash
./hydra secrets init --chain-id 4488 --data-dir node-secrets
```

This generates secrets and stores them in `node-secrets`. You will set a password for encryption.

#### Output keys later (if needed)

Private keys:

```bash
./hydra secrets output-private --data-dir node-secrets
```

Public data (EVM Address) + Node ID:

```bash
./hydra secrets output-public --data-dir node-secrets
```

***

### 4) Configure the node

#### Genesis file (`genesis.json`)

The genesis file is critical. **Do not alter it**. In the new releases, the genesis file is built into the hydra executable and as such does not need a custom Genesis file. For visibility, you can find the latest HydraChain Mainnet genesis file at the [following location](https://github.com/Hydra-Chain/hydragon-node/blob/testnet/chain/public-configs/genesis-mainnet.json).

#### Secrets manager config (`secretsManagerConfig.json`)

Generate a secrets manager config for encrypted-local secrets. This also includes a CoinGecko API key used for the Hydra Price Oracle feature. A free API key can be generated at CoinGecko's [API page](https://www.coingecko.com/en/api).

```bash
./hydra secrets generate --type encrypted-local --name node --extra "coingecko-api-key=<Insert key here>"
```

***

### 5) Launch the node (and wait for sync)

Run the node:

```bash
./hydra server --data-dir ./node-secrets --chain mainnet --grpc-address :9632 --libp2p 0.0.0.0:1478 --jsonrpc 0.0.0.0:8545 --secrets-config ./secretsManagerConfig.json
```

**Chain flags:**

* Use `--chain mainnet` for Mainnet.
* Use `--chain testnet`  if using Testnet.
* If ever instructed to use a Custom genesis: `--chain "custom:<path_to_genesis_file>"`

> ⏳ First sync can take time—wait until your node is fully synced before registering as a validator.

***

### 6) Prepare your validator account

After your node is operational and fully synced, you're ready to become a validator. This requires:

* **Mainnet:** Fund your new validator address with a minimum of 15,000 HYDRA, plus some extra for transactions fees.
* **Testnet only:**  Fund your validator address using the [Faucet](https://testnetapp.hydrachain.org/faucet/).

***

### 7) Register and stake as validator

Hydra requires a minimum **15,000 HYDRA** stake for validators.

#### Register + self-stake + set commission

```bash
./hydra hydragon register-validator --data-dir ./node-secrets --stake 15000000000000000000000 --commission 10 --jsonrpc http://localhost:8545
```

> 🧠 Amounts are specified in **wei**. (15,000 HYDRA = 15000 × 10^18 wei.)

#### Stake with vesting (optional, higher rewards)

You can lock funds for **1–52 weeks** to receive a loyalty bonus. Early unstake penalty is **0.5% per remaining week**, and rewards distributed during the vesting period are burned on early exit. The below command can be run only after you have registered and self staked as a validator

Example (52 weeks vesting with additional 15,000 HYDRA):

```bash
./hydra hydragon stake --data-dir ./node-secrets --self true --amount 15000000000000000000000 --vesting-period 52 --jsonrpc http://localhost:8545
```

The above example will vest your existing staked amount 15,000 HYDRA, plus an additional 15,000 HYDRA. If you wish to only vest the original 15,000 HYDRA, then you can do that by setting the `--amount` to 0 like below

```bash
./hydra hydragon stake --data-dir ./node-secrets --self true --amount 0 --vesting-period 52 --jsonrpc http://localhost:8545
```

***

### 8) Ongoing validator operations (must-know commands)

#### Update commission (two-step, with 15-day delay)

1. Set pending commission:

```bash
./hydra hydragon commission --data-dir ./node-secrets --commission 15 --jsonrpc http://localhost:8545
```

2. After the 15 day waiting period, apply:

```bash
./hydra hydragon commission --data-dir ./node-secrets --apply true --jsonrpc http://localhost:8545
```

#### Claim validator rewards + delegator commission rewards

Claim validator rewards:

```bash
./hydra hydragon claim-rewards --data-dir ./node-secrets --jsonrpc http://localhost:8545
```

Claim commission earned from delegators:

```bash
./hydra hydragon commission --data-dir ./node-secrets --claim true --jsonrpc http://localhost:8545
```

***

### 9) Ejection / Ban recovery (read this before you need it)

Hydra includes an ejection + ban mechanism to reduce network stall risk and maintain sub-second block time.

* Initial ejection can trigger at \~**18,000 blocks (\~2 hours)** depending on block time.
* If not reactivated within \~**259,200 seconds (\~72 hours)** you will be **permanently banned**.
* Current penalty: **1,000 HYDRA**, with **700 burned** and **300** as reporter reward (in some cases).

#### Re-activate after ejection

After fixing the issue and re-syncing your node:

```bash
./hydra hydragon terminate-ban --data-dir ./node-secrets --jsonrpc http://localhost:8545
```

#### Withdraw penalized funds (if banned)

Initiate withdrawal:

```bash
./hydra hydragon withdraw --penalized-funds true --data-dir ./node-secrets --jsonrpc http://localhost:8545
```

After the withdrawal period of 7 days:

```bash
./hydra hydragon withdraw --data-dir ./node-secrets --jsonrpc http://localhost:8545
```

Withdraw using `--banned`:

```bash
./hydra hydragon withdraw --data-dir ./node-secrets --banned --jsonrpc http://localhost:8545
```

> 💡 If your machine is down, you can use a public RPC as the `--jsonrpc` value.&#x20;
>
> For Instance, replace `--jsonrpc http://localhost:8545` with  `--jsonrpc https://rpc-mainnet.hydrachain.org`

***

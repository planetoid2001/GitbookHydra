# Add & Remove Liquidity

On [HydraDEX](https://hydradex.org/), you can add and concentrate your liquidity within a custom price range, or throughout the entire price range from 0 to infinity. HydraDEX is also accessible on Mobile, on any of your favourite EVM Wallets. You can bridge in assets from the Ethereum Blockchain using the native [Hydra Bridge](https://multibridge.hydrachain.org/).

### What is a Liquidity pool?

A liquidity pool is a pair of tokens locked in a smart contract and is used for trades on a Decentralized Exchange or DEX like [HydraDEX](https://hydradex.org/). These tokens in the pool are provided by Liquidity Providers (LP's), who receive LP Tokens (V2 Pools) or an LP NFT (V3 pools) as proof of liquidity.

The LP's earn fees from trades that occur on the pools they have their liquidity in. For some pools, there are also attractive [Liquidity Mining incentives](https://docs.hydrachain.org/hydradex/liquidity-mining) provided to the Liquidity Providers as a reward for supplying liquidity.

Let's dive in&#x20;

### Adding Liquidity on HydraDEX V3

1. Log in to your Wallet on your Laptop or your mobile wallet app (Like MetaMask or Rabby) and choose the address that you will use for accessing the HydraDEX.

2. Visit <https://hydradex.org/> and click on the "Pools" tab. If using a mobile wallet like MetaMask or Rabby, please use your wallets in-build browser.

3. Click on "New Position" and and from the dropdown, select the token pair you wish to add liquidity for (For example HYDRA and USDC). You can visit the info site at <https://info.hydradex.org/> to view information like TVL, token price, trading volume, fee tier etc... on all existing Liquidity pools.<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FuMoHUPlxGDgCf2pz8fcP%2F1New_Position.PNG?alt=media&#x26;token=41598a8c-e319-4621-ac41-e17a8c661485" alt=""><figcaption><p>Click on "New Position"</p></figcaption></figure>

   <br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FRLv9noZTDw1CyErtt20S%2F2Add_Liquidity.PNG?alt=media&#x26;token=6f671ec0-c63d-4303-960a-6b8f26eda71a" alt=""><figcaption><p>Choose a Pair</p></figcaption></figure>

4. Select the Fee tier for the pool. There are 4 available fee tiers 0.01%, 0.05%, 0.3%, 1%. You can view existing pool fee tiers on the info page and choose the appropriate one. \
   You may also want to consider which fee tiers have [active liquidity mining campaigns](https://docs.hydrachain.org/hydradex/liquidity-mining) running which can bee seen on the "[Stake](https://hydradex.org/#/stake)" Tab.\
   \
   If the pool already exists, then your liquidity position will be added to the pool. If the pool does not exist, your liquidity position will create a new pool at the selected fee tier.<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2Fv0GxJwCdItV0VjbqgK22%2F2Add_Liquidity_selection.PNG?alt=media&#x26;token=4bd03a29-e199-4a7a-b114-8fc799fc78e2" alt=""><figcaption><p>Select a Fee Tier</p></figcaption></figure>

5. Type in the price range for which you would like to provide liquidity. You can enter a specific concentrated range (like in the picture below) or the full price range from 0 to infinity, although this is not capital efficient. If you want to deploy liquidity on the full price range, click on "Full Range"\
   \
   **Note:** When selecting a price range, the price will round to the nearest tick.\
   \
   If the market price moves out of your set range, then your liquidity position will end up fully converted into one of the two assets and stop earning fees. Please view an example in the [below section **here**](https://docs.hydrachain.org/hydradex/add-and-remove-liquidity#price-range-selection).<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FaW5Q52y32OzsY48IAfY1%2F3Add_Liquidity_selection.PNG?alt=media&#x26;token=bbd79bea-35ab-4610-b77b-4a5a3ac82b17" alt=""><figcaption><p>Enter Minimum and Maximum Price</p></figcaption></figure>

6. Enter the amount of tokens you want to deposit into the liquidity pool, or select “Max” for the maximum amount of tokens. See below illustration<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FPzrfAwIop25ztht61Tj1%2F4Add_Liquidity_amounts.PNG?alt=media&#x26;token=dcb3eff3-d290-4f0f-a682-e08be63e5a92" alt=""><figcaption><p>Enter amount of tokens for LP</p></figcaption></figure>

7. Click on "Approve" and sign the transaction in your wallet and wait for half a second (Yes, Hydra is that Fast 🚀). This gives the DEX permission to use the tokens for providing liquidity . You may need to approve for both tokens and will shows buttons accordingly. Please note, this transaction will cost some minimal network fees.<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FGsSZx98anIO91mshhYp5%2F5Add_Liquidity_approve.PNG?alt=media&#x26;token=2f7f4723-0c91-4f23-87f7-0bdb9ad15bf7" alt=""><figcaption><p>Click on Approve</p></figcaption></figure>

8. Next you need to click on "Preview" to review the liquidity position details, and then click on "Add". Please note, this transaction will cost some network fees.\ <br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2F837n1h1IYQqdk8yAdl6f%2F6Add_Liquidity_preview.PNG?alt=media&#x26;token=853bff7b-bc1d-40a7-b458-a6b3e8e7d619" alt=""><figcaption><p>Review your LP details and click on Add</p></figcaption></figure>

9. Once the transaction is confirmed, you will be able to see your liquidity position on the Pool tab.\ <br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FzqE5vheGy4AqxvJA7KHJ%2Fimage.png?alt=media&#x26;token=503cc42a-479f-4e86-9756-478f998ef617" alt=""><figcaption><p>Liquidity Position on the Pool Tab</p></figcaption></figure>

   <br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FOZaLkq2oXxB4EPpPfevL%2F7Postion_Details.PNG?alt=media&#x26;token=954b31b6-1c9e-428f-aa3a-dc36eb52e60b" alt=""><figcaption><p>Position Details</p></figcaption></figure>

10. Check out the [Liquidity Mining Campaigns](https://docs.hydrachain.org/hydradex/liquidity-mining) for certain pairs at select fee tiers ✨

***

## Useful Information

### What is Impermanent Loss?

Impermanent Loss takes place when the relative value (to each other) of your deposited tokens changes compared to when you entered the liquidity pool. The higher the relative change in price of the tokens, the higher the effect of impermanent loss.&#x20;

**Example:** Myra provides 500 HYDRA and 200 USDC to a HYDRA / USDC Liquidity Pool. And the value of 500 HYDRA is $200 (1 HYDRA= $0.4). So in total, Myra has provided liquidity worth $400.\
\
Let's say the price of HYDRA increases to $4. Now due to the nature of automated market making (AMM) in DEX's, the ratio of the provided liquidity has changed as the result of the trades that caused the price to increase.\
\
When Myra decides to withdraw her liquidity from the pool at the increased HYDRA price of $4, the balance has turned into 200 HYDRA and 800 USDC; and that is worth $1600! These profit's are quite good as she put in $400 worth of liquidity and got $1600! but wait! What would be her profit, if she would have just HODL'ed those tokens? The combined value would have been $2200 now. Myra would have been better off HODL'ing the tokens instead of depositing into the liquidity pool. This is what is called Impermanent Loss.

Liquidity mining campaigns help towards negating the impact from Impermanent loss. Check out the [Liquidity mining campaigns](https://docs.hydrachain.org/hydradex/liquidity-mining) available on the [HydraDEX](https://hydradex.org/).

{% hint style="warning" %}
**In the above example, we assumed that Myra has provided liquidity across the full price range and we have not considered income from Fees and Liquidity Mining rewards.**
{% endhint %}

### Price Range Selection

Your position only earns fees during periods where the market price is within the price range you set. \
For example: If you set a price range of $1 — $5 for HYDRA/USDC and HYDRA price falls to 0.9, then your liquidity position balance will be entirely in Hydra.\
\
Conversely, if HYDRA appreciates to $6, then your liquidity position balance will be entirely in USDC. Additionally, while the price remains outside of your price range, your position will be "inactive". This means your position will not earn fees until the market price comes back in range.\
\
Therefore it is important to manage your liquidity positions accordingly. You can always remove the liquidity from your current position and create a new position with a more efficient price range.

### Tighter Ranges gets you higher fees

With tighter ranges you earn a higher proportion of the fees and also a higher share of the [Liquidity Mining](https://docs.hydrachain.org/hydradex/liquidity-mining-on-hydradex) budget of the pool; however, It also acts as a form of leverage on impermanent loss, since the capital concentration of your assets is amplified. If your range is breached by the price, you will end up owning 100% of the underperforming asset.

Example: If you set a price range of $1 — $5 for HYDRA/USDC and HYDRA price falls to 0.9, then your liquidity position balance will be entirely converted into HYDRA. Conversely, if Hydra appreciates to $6, then your liquidity position balance will be entirely converted into USDC. \
\
Additionally, while the price remains outside of your price range, your position will be "inactive". This means your position will not earn fees or Liquidity mining rewards (if participating) until the market price comes back into range. As mentioned earlier, you can remove the liquidity from your current position and add a new position selecting a more preferred price range.

If you have any questions, please do no hesitate to contact an Admin on the official Telegram group <https://t.me/hydrachain>

\ <br>

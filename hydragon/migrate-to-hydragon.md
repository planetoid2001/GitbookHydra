# Migrate to HydraGon

### **Steps to Migrate using the Hydra Bridge**

#### **Step 1: Install the Hydra Browser Extension Wallet and MetaMask**

1. Download the [**Hydra Browser Wallet Extension**](https://chromewebstore.google.com/detail/hydrawallet/polcbnennmbhbdoafiicjgccofalcncl) from the Chrome Web Store on **Microsoft Edge** or **Brave** and install it. [Hydra Wallet Extension](https://chromewebstore.google.com/detail/hydrawallet/polcbnennmbhbdoafiicjgccofalcncl).&#x20;
   1. If the Extension is not available on the Chrome Web Store in your region, then download it from <https://hydrachain.org/extension> and follow the below short steps:
      1. Unzip the folder
      2. On Edge or Brave, go to Manage Extensions and Turn on developer mode
      3. Click on Load unpacked and select the 0.0.10\_0 Folder from the unzipped downloaded folder
2. Follow the setup process to **import an existing wallet** using your **private key.**\
   \
   ![](main/images/2Migrate/1import%20an%20existing%20wallet.png) ![](main/images/2Migrate/2privatekey.png)
   1. You can obtain the private key for your address from the Hydra Mobile app. Swipe the address to the right, to reveal the private key (click the eye to authenticate and display)![](main/images/2Migrate/3viewpkey.png)
   2. If you are using the legacy Desktop Client, then [export your private key](https://docs.hydrachain.org/staking-hydra-coins/setting-up-staking#step-4.-exporting-your-private-key) from the console or CLI.
3. Install MetaMask from <https://metamask.io/download/> and follow the steps to create a wallet, if you do not have one already. If you already use and control an EVM (Ethereum) address, then you can use the same address.
   1. On MetaMask, you will need to "Add a custom network". The Hydra Chain Network Information is available on Chainlist <https://chainlist.org/chain/4488> and can be added from there in one click
   2. To add the network manually, Click on the Top left Ethereum Icon, and click on "Add a custom network" and add the below network information:&#x20;

      * Network Name: Hydra Chain&#x20;
      * Default RPC URL: <https://rpc-mainnet.hydrachain.org&#x20>;
      * Chain ID: 4488&#x20;
      * Currency Symbol: HYDRA&#x20;
      * Block explorer URL: <https://skynet.hydrachain.org>

      &#x20;  ![](main/images/2Migrate/4selecthydra.png)      ![](main/images/2Migrate/5selectnetwork.png)

#### **Step 2: Connect to the MultiBridge**

1. Sign in to your Hydra Browser Extension and login to your address.\
   \
   ![](https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FUP3nRE2GzMgOK0l8s23a%2Fimage.png?alt=media\&token=36f3953c-5148-4c7b-8cce-c8c15fb2f776)<br>
2. Open the **Hydra MultiBridge** on the same browser: <https://multibridge.hydrachain.org/> The Extension will automatically connect to the MultiBridge.

<figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FjeH3QUrZjn5HoUqSnbL4%2Fimage.png?alt=media&#x26;token=5bbe2c53-a0f5-4c4a-a3c9-5dd3d42155e2" alt=""><figcaption><p>Hydra MultiBridge</p></figcaption></figure>

#### **Step 3: Bridge HYDRA to HydraGon**

1. Select **Hydra** as the origin chain and **HydraGon** as the destination chain.
2. Choose the coin (HYDRA) or token (LOC, CHANGE, wBTC, wETH, USDC, USDT or DAI) from the dropdown and specify the amount you wish to bridge.
3. In the "Destination wallet address" box, Input your **MetaMask wallet address** (this will be the destination of the bridged funds). Please ensure that you are entering the correct address that you have access to
4.

```
<figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2F3p6BtVIgTPKbX1MFVHCg%2Fmultibridge2.PNG?alt=media&#x26;token=495a3761-32f5-4681-ad94-d5d22977c518" alt=""><figcaption><p>Select Hydra to HydraGon. Enter Address &#x26; Amount</p></figcaption></figure>
```

5. Click on "Approve", confirm the subsequent pop-up & wait for the transaction to process<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2F3EfFi7q6vPScyZfpToes%2Fimage.png?alt=media&#x26;token=9115ad56-6369-468c-8a69-2acfda5bc34a" alt=""><figcaption><p>Click on Approve and then "Confirm" the pop-up</p></figcaption></figure>
6. The "Approve" button will change to "Transfer". Click on "Transfer" and confirm the subsequent pop-up to initiate the migration / bridging process.<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FArhJaKOWjVg9HcRvPgWk%2Fimage.png?alt=media&#x26;token=bff978ce-9e73-4376-9ced-46e587e4c2db" alt=""><figcaption><p>Click on Transfer and then "Confirm" the pop-up</p></figcaption></figure>
7. The migration will take between 15 to 45 minutes to process. Sometimes it may take longer (upto 2 hours) during congestion. You can verify receipt of funds by checking your HYDRA balance in your MetaMask wallet or the Skynet Explorer: <https://skynet.hydrachain.org/> or <https://skynet2.hydrachain.org/>\
   \
   ![](https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2F3FVF4VL77RIamHBO63sZ%2Fimage.png?alt=media\&token=aa17e46d-1979-44c2-b24a-5e8cc0e4a8e8)![](https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2FPgqAdDLLJlEQwguRAIb9%2Fimage.png?alt=media\&token=131fdbc5-fea1-474e-aac9-469424c8dc14)<br>

### Troubleshooting for Known Situations / Issues

#### There are a few known situations for some users. This is related to the legacy Bitcoin UTXO tech stack on the legacy Blockchain and can be solved in a few ways. Some of these issues are:

1. Legacy wallet addresses that have too many UTXO's
2. Legacy wallet addresses that were staking using the staking client
3. Rare instances of Incorrectly calculated balances due to faulty UTXO interpretation on very few Legacy wallet addresses

{% hint style="info" %}
Stakers whose addresses were staking using the Hydra Desktop Staking Client will need to use the Staking Client to consolidate their HYDRA
{% endhint %}

The solution to all of the above situations is to consolidate all your UTXO's. This can be done in 4 ways

1. Bridge your HYDRA in several transactions and not in one transaction
   1. For Example: if you have 50,000 HYDRA, then bridge 10,000 or 20,000 HYDRA at a time (Increase the amount if you do not get any errors OR Reduce the amount accordingly if you get errors towards the last remaining balance).
2. Send your entire HYDRA Balance to yourself. This will combine all the UTXO's into one big clean UTXO, however may not work if there are too many UTXO's. In this case, see next point.
3. Send your HYDRA Balance in parts, to another Hydra address that you own and control Or create a new address on the Hydra Mobile App and send the HYDRA to that new address.\
   \
   For Example: if you have 50,000 HYDRA, you can send the HYDRA to a new address in 5 parts of 10,000 HYDRA each
4. Mint and Burn Lydra incrementally using the Legacy Desktop staking client, which performs the same task of combining UTXO's and at a much lower transaction fee.\
   \
   For Example: if you have 50,000 HYDRA
   1. Click on Help-> Information Window -> Console Tab
   2. Command to mint Lydra is \
      `mintlydra "HX1GkJdye9WoUnrE2v6ZQhQ72EUVDtGXQX" 15000` \
      (Replace the Address and amount accordingly)\
      ![](https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2Fk4rCwq2xz02qbMQnv1uc%2Fimage.png?alt=media\&token=27b89590-cc77-4239-9c20-5c42ca85c9a4)\
      \
      Command to burn Lydra is\
      `burnlydra "HX1GkJdye9WoUnrE2v6ZQhQ72EUVDtGXQX" 15000`\
      (Replace the Address and amount accordingly)\
      ![](https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2F9p9WFofn0aKgxVJWPMUS%2Fimage.png?alt=media\&token=e5096d6c-6131-4114-b4dd-a50d580e69b4)<br>
   3. Mint 25,000 LYDRA, then burn 25,000 LYDRA
   4. Mint 45,000 LYDRA, then burn 45,000 LYDRA
   5. Mint approximately 49,850 HYDRA (Reduce amount slightly if you get an error), then burn the same amount you minted
   6. These steps will consolidate most of the UTXO's into few big UTXO's. After the last burn, Send your entire HYDRA Balance to yourself from the Send tab of the staking client
   7. If you have less than 320 UTXO's on your address, then you can Mint and Burn the Lydra in just 2 transactions\
      `mintlydra "HX1GkJdye9WoUnrE2v6ZQhQ72EUVDtGXQX" -1`\
      \
      Wait for the mint to complete, then\
      \
      `burnlydra "HX1GkJdye9WoUnrE2v6ZQhQ72EUVDtGXQX" -1`
   8. &#x20;You can check the UTXO count by navigating to the Send Tab and click on the "INPUTS" button, and choose the "Tree Mode". If you do not see the Inputs button, then you can enable it by clicking on Settings -> Options -> Select the Wallet Tab -> Check the "Enable coin control features" box and click on Ok.<br>

If you do not have the Hydra Desktop Client installed, then follow this Recovery Flow, to setup the Desktop Client on your local Laptop relatively quickly&#x20;

1. Download and install the latest version of the Desktop client as per your Operating System [\[Link Here\]](https://github.com/Hydra-Chain/node/releases/tag/hydra_v0.20.20)
2. &#x20;Download this Backup Data Directory, which has data untill the 10th of December 2024, which will help you load the Hydra Desktop client quickly [\[Link here\]](https://hydrachain.org/backup)
3. After launching the client, it will start loading the blockchain from scratch. At this point, **Exit** the Client and wait for 2 minutes.
4. Navigate to the Data directory on your laptop
   1. For Windows: C:\Users\your\_username\AppData\Roaming\HYDRA
   2. For Linux: \~/.hydra
   3. For Mac: \~/Library/Application Support/hydra
   4. For Raspberry Pi: /home/pi/.hydra
5. Delete all the Files in this Hydra Folder EXCEPT the wallet.dat file
6. From the downloaded Backup Data Directory, unzip the content and copy & paste the files into the Hydra folder which only has the wallet.dat file. It will then look like this below<br>

   <figure><img src="https://2559938628-files.gitbook.io/~/files/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-MLNXvXNFPLXIrp6TqdS%2Fuploads%2F3el3vGtRq55zgEVvdqi4%2Fimage.png?alt=media&#x26;token=f0f5487e-743c-400e-b010-976c60b1aeb3" alt=""><figcaption></figcaption></figure>
7. Now launch the staking client. It should ideally start up within a few minutes. The backup data is until 10th December 24, so it should update pretty quickly.&#x20;
8. After the client is fully updated, then [import your address via the console](https://docs.hydrachain.org/hydra-for-beginners#importing-your-private-key) using your private key

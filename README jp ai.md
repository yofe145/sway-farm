スウェイファーム
Swayで書かれたシンプルな農業ゲーム。

ローカルで実行する
Fuelupがインストールされており、ベータ5ツールチェーンを使用していることを確認してください。

Fuel Wallet拡張機能をインストールし、ウォレットアドレスをコピーします。 フロントエンドフォルダーで、src/Appを開きます。tsxファイルを作成し、Fuel walletアドレスを使用して次の行を追加します:

新しいWalletLocked("fuel123....");
コンソール。ログ("WALLET:",myWallet.アドレス。トビ256());
フロントエンドをnpm startでローカルに実行し、コンソールをチェックしてFuel walletアドレスをB256形式で確認します。 このアドレスをコピーし、chainconfigの以下に示すようにownerフィールドを更新します。あなたの財布がテスト資金を持つようにjsonファイル。

"initial_state":{
"コイン":[
{
"所有者":"0x_your_fuel_wallet_address",
"金額":"0x00000000fffffff",
"asset_id":"0x0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 0 00000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000"
}
]
},
ローカルノードを起動するには、メインプロジェクトフォルダで以下のコマンドを実行します。

fuel-core run--db-type in-memory--chain./chainConfig.json
次に、contractフォルダで、以下のコマンドを実行して、ローカルノードにcontractを展開します。

forcデプロイ--unsigned
あなたの財布には、とネットワークを追加しますhttp://127.0.0.1:4000/graphql そして、そのネットワークに切り替えます。

コントラクトIDは、frontend/src/constantsのCONTRACT_IDと一致する必要があります。ts. コントラクトを更新してコントラクトIDが変更された場合は、ここで更新し、フロントエンドフォルダーで以下のコマンドを実行して新しいタイプを生成する必要があります。

npx-i型。./contract/out/debug/*-abi.-----------/src/契約






# sway-farm

A simple farming game written in Sway.

## Running Locally

Make sure you have `fuelup` installed and are using the `beta-5` toolchain. 

Install the Fuel Wallet extension and copy your wallet address. In the frontend folder, open the `src/App.tsx` file and add the following lines using your Fuel wallet address:

```javascript
const myWallet = new WalletLocked("fuel123....");
console.log("WALLET:", myWallet.address.toB256());
```

Run the frontend locally with `npm start`, and check your console to see your Fuel wallet address in B256 format. Copy this address and update the `owner` field as shown below in the `chainConfig.json` file so that your wallet will have test funds.

```json
"initial_state": {
      "coins": [
        {
          "owner": "0x_YOUR_FUEL_WALLET_ADDRESS",
          "amount": "0x00000000FFFFFFFF",
          "asset_id": "0x0000000000000000000000000000000000000000000000000000000000000000"
        }
      ]
    },
```

Run the command below in the main project folder to start a local node.

```shell
fuel-core run --db-type in-memory --chain ./chainConfig.json
```

Next, in the `contract` folder, run the command below to deploy the contract to your local node.

```shell
forc deploy --unsigned
```

In your wallet, add a network with `http://127.0.0.1:4000/graphql` and switch to that network.

The contract ID should match the `CONTRACT_ID` in `frontend/src/constants.ts`. If you update the contract and the contract ID changes, you must update it here and run the command below in the `frontend` folder to generate new types.

```shell
npx fuels typegen -i ../contract/out/debug/*-abi.json -o ./src/contracts
```

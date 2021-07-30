<template>
  <div class="home">
    <img src="../assets/logo.svg" width="300" /><br /><br />
    --<br /><br />
    <div v-if="!account">
      <b-button type="is-primary" v-on:click="switchNetwork('quadrans')"
        >Connect to Mainnet</b-button
      ><br /><br />
      <b-button type="is-primary is-light" v-on:click="switchNetwork('ticino')"
        >Connect to Testnet</b-button
      >
    </div>
    <div v-if="account">
      {{ account }}<br />
      {{ balance }} QDC <br /><br />
      --
      <br /><br />
      <b-button type="is-primary" v-on:click="disconnect()"
        >Disconnect</b-button
      >
    </div>
    <br />--<br /><div style="font-size: 12px">
      This is an
      <a href="https://github.com/quadrans/quadrans-connect" target="_blank"
        >open-source</a
      ><br>
      project made with ❤️ by<br>
      <a href="https://quadrans.io" target="_blank">Quadrans Foundation</a>
    </div>
  </div>
</template>


<script>
import Web3 from "web3";
export default {
  data() {
    return {
      selected_network: "",
      account: "",
      web3: "",
      balance: 0,
    };
  },
  methods: {
    async connect() {
      const app = this;
      if (window.ethereum) {
        // Check if network is desired one
        app.selected_network = await app.web3.eth.net.getId();
        // Request accounts
        await window.ethereum.send("eth_requestAccounts");
        // Read accounts
        const accounts = await app.web3.eth.getAccounts();
        if (accounts[0] !== undefined) {
          app.account = accounts[0];
          // Take balance
          const balance = await app.web3.eth.getBalance(accounts[0]);
          app.balance = parseFloat(
            app.web3.utils.fromWei(balance, "ether")
          ).toFixed(10);
          localStorage.setItem("connected", app.account);
        }
      } else {
        alert("Please install Metamask");
      }
    },
    async disconnect() {
      const app = this;
      localStorage.removeItem("connected");
      app.account = "";
      app.balance = 0;
      location.reload();
    },
    async switchNetwork(what) {
      const app = this;
      if (what === "quadrans") {
        await window.ethereum.request({
          method: "wallet_addEthereumChain",
          params: [
            {
              chainId: "0x2AC2",
              chainName: "Quadrans",
              rpcUrls: ["https://rpc.quadrans.io"],
              nativeCurrency: {
                name: "Quadrans Coin",
                symbol: "QDC",
                decimals: 18,
              },
              blockExplorerUrls: ["https://explorer.quadrans.io/"],
            },
          ],
        });
      } else if (what === "ticino") {
        await window.ethereum.request({
          method: "wallet_addEthereumChain",
          params: [
            {
              chainId: "0x2AC3",
              chainName: "Quadrans - Testnet",
              rpcUrls: ["https://rpctest.quadrans.io"],
              nativeCurrency: {
                name: "Quadrans Coin - Testnet",
                symbol: "tQDC",
                decimals: 18,
              },
              blockExplorerUrls: ["https://explorer.testnet.quadrans.io/"],
            },
          ],
        });
      }
      app.connect();
    },
  },
  async mounted() {
    const app = this;
    if (window.ethereum) {
      app.web3 = await new Web3(window.ethereum);
      const accounts = await app.web3.eth.getAccounts();
      if (accounts.length > 0) {
        if (accounts[0] === localStorage.getItem("connected")) {
          const balance = await app.web3.eth.getBalance(accounts[0]);
          app.account = accounts[0];
          app.balance = parseFloat(
            app.web3.utils.fromWei(balance, "ether")
          ).toFixed(10);
        }
      }
    }
  },
};
</script>

<template>
  <div>
    <p>Substrate Polkadot</p>
    <p>{{ getHead }}</p>
    <md-button class="md-primary">Check Status</md-button>
  </div>
</template>

<script>
import { ApiPromise, WsProvider } from '@polkadot/api';

const WS_PROVIDER = 'wss://poc3-rpc.polkadot.io/';
const provider = new WsProvider();
const api = ApiPromise.create(provider);

export default {
  name: 'MainPage',
  data() {
    return {
      isReady: false,
      apiClient: null,
    };
  },
  computed: {
    getHead() {
      return api.rpc.chain.subscribeNewHeads(header => {
        console.log(`Chain is at ${header.number}`);
        return header.number;
      });
    },
  },
};
</script>

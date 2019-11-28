<template>
  <div>
    <p>Substrate Polkadot</p>
    <p>{{ getHead }}</p>
    <md-button class="md-primary">Check Status</md-button>
  </div>
</template>

<script>
import { ApiRx, ApiPromise, WsProvider } from '@polkadot/api';

const WS_PROVIDER = 'wss://poc3-rpc.polkadot.io/';
const provider = new WsProvider(WS_PROVIDER);
const api = ApiRx.create(provider).toPromise();

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
      return api;
    },
  },
};
</script>

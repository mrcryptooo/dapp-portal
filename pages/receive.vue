<template>
  <div>
    <PageTitle :fallback-route="{ name: 'receive-methods' }">Your address</PageTitle>
    <ConnectWalletBlock v-if="!isConnected">Connect wallet to view your address</ConnectWalletBlock>
    <Receive v-else :address="address" :destination="destinations.era" />
  </div>
</template>

<script lang="ts" setup>
import { computed } from "vue";

import { storeToRefs } from "pinia";

import { useDestinationsStore } from "@/store/destinations";
import { useOnboardStore } from "@/store/onboard";
import Receive from "@/views/transactions/Receive.vue";

const { account, isConnected } = storeToRefs(useOnboardStore());
const { destinations } = storeToRefs(useDestinationsStore());

const address = computed(() => account.value.address || "");
</script>

<script setup lang="ts">
// import Spinner from "@/components/ui/spinner/spinner.vue";

import {delay, deviceName, mode, serialNumber} from "@/util/mockup.ts";
import {alsData, settingsData} from "@/state/state.ts";

import { onMounted } from 'vue';
// import MainPage from "@/components/MainPage.vue";
// import ModernTheme from "@/components/ModernTheme.vue";
// import ClassicTheme from "@/components/ClassicTheme.vue";
// import HelloWorld from "@/components/HelloWorld.vue";

import {useColorMode} from '@vueuse/core'
const colorTheme = useColorMode()


onMounted(syncMockDataToState);

function syncMockDataToState() {
  settingsData.startLoading()
  // Sinkronisasi mode
  
  alsData.setDelayALS(delay)
  alsData.setModeALS(mode)
  alsData.setDeviceNameALS(deviceName)
  alsData.setSerialDeviceALS(serialNumber)

  colorTheme.value = 'dark'

  settingsData.stopLoading()
}




</script>

<template>
  <router-view></router-view>
</template>

<style scoped>

</style>

<script setup lang="ts">
import {useColorMode} from '@vueuse/core'
import {ref, watchEffect  } from 'vue';
import MainHeader from "@/components/content/MainHeader.vue";
// import { Card, CardContent, CardDescription, CardHeader, CardTitle } from '@/components/ui/card'
import {
  AlertDialog,
  AlertDialogAction,
  AlertDialogCancel,
  AlertDialogContent,
  AlertDialogDescription,
  AlertDialogFooter,
  AlertDialogHeader,
  AlertDialogTitle,
  AlertDialogTrigger,
} from '@/components/ui/alert-dialog';

import {availableMode} from "@/util/mockup.ts";
import {alsData} from "@/state/state.ts";
import {Label} from "@/components/ui/label";
import {Siren} from "lucide-vue-next";
import {RadioGroup, RadioGroupItem} from "@/components/ui/radio-group";
import { Slider } from '@/components/ui/slider';
import { Button } from '@/components/ui/button';
import { Input } from '@/components/ui/input';

const temaMode = useColorMode()
temaMode.value = 'dark'

function findModeNameByValue(value: string) {
  const foundMode = availableMode.find(item => item.value === value);
  return foundMode ? foundMode.name : null;
}

const inputSlider = ref([alsData.delayALS.value]);

watchEffect(() => {
  alsData.delayALS.value = inputSlider.value[0]
});
</script>

<template>
  <div class="flex min-h-screen w-full flex-col">
    <MainHeader></MainHeader>
    <main class="flex flex-1 flex-col gap-3 p-4 md:gap-3 md:p-8">
      <section>
        <div class="mx-auto flex max-w-[980px] flex-col items-center gap-2 py-8 md:py-12 md:pb-8 lg:py-24 lg:pb-20 page-header pb-8 page-header pb-8">
          <h1 class="text-center text-3xl font-bold leading-tight   md:block"> Informasi Alat </h1>
        </div>
        <div class="grid gap-2 grid-cols-3 text-center">
          <div>
            <h1 class="text-xs">Nama Device</h1>
            <p class="font-bold text-lg ">{{ alsData.deviceNameALS.value }}</p>
          </div>
          <div>
            <h1 class="text-xs">Serial Number</h1>
            <p class="font-bold text-lg ">{{alsData.deviceSerialALS.value}}</p>
          </div>
          <div>
            <h1 class="text-xs">Jumlah Channel</h1>
            <p class="font-bold text-lg ">{{ alsData.deviceChALS.value}}</p>
          </div>
        </div>
        <div class="grid gap-2 mt-2  grid-cols-1 text-center">
          <AlertDialog>
            <AlertDialogTrigger as-child>
              <Button class="w-2/5 mx-auto  py-2" variant="link">
                Ganti Device
              </Button>
            </AlertDialogTrigger>
            <AlertDialogContent>
              <AlertDialogHeader>
                <AlertDialogTitle>Ganti Informasi Device</AlertDialogTitle>
                <AlertDialogDescription>
                  <Label for="device" class="text-left mt-2">Nama Device Baru</Label>
                  <Input id="device" type="text" class="my-5 font-bold" placeholder="Nama Device" v-model="alsData.deviceNameALS.value" />
                </AlertDialogDescription>
              </AlertDialogHeader>
              <AlertDialogFooter>
                <AlertDialogCancel>TIdak Jadi</AlertDialogCancel>
                <AlertDialogAction>Simpan</AlertDialogAction>
              </AlertDialogFooter>
            </AlertDialogContent>
          </AlertDialog>

        </div>
      </section>
      <section>
        <div class="mx-auto flex max-w-[980px] flex-col items-center text-center gap-2 py-4 md:py-12 md:pb-8 lg:py-24 lg:pb-20 page-header pb-8 page-header pb-8">
          <h1 class="text-center text-3xl font-bold leading-tight   md:block"> Ganti Mode </h1>
          <div class="mt-3">
            <h1 class="text-xs">Mode Sekarang</h1>
            <p class="font-bold text-lg ">MODE : {{ findModeNameByValue(alsData.modeALS.value) }}</p>
          </div>
        </div>
          <RadioGroup v-model="alsData.modeALS.value" class="grid mt-2 py-2 text-center  grid-cols-4 gap-4">
            <template v-for="item in availableMode" :key="item.value">
              <div>
                <RadioGroupItem :id="item.value" :value="item.value" class="peer sr-only"/>
                <Label
                    :for="item.value"
                    :class="[
                                  'flex flex-col items-center text-md justify-between rounded-md border-2 border-muted bg-popover p-4 hover:bg-accent hover:text-accent-foreground',
                                  {'peer-data-[state=checked]:border-primary': true, '[&:has([data-state=checked])]:border-primary': true}
                                ]"
                >
                  <Siren class="h-6 w-6 text-muted-foreground"/>
                  {{ item.name }}
                </Label>
              </div>
            </template>
          </RadioGroup>
      </section>
      <section>
        <div class="mx-auto flex max-w-[980px] flex-col items-center gap-2 py-2 md:py-12 md:pb-8 lg:py-24 lg:pb-20 page-header pb-8 page-header pb-8">
          <h1 class="text-center text-3xl font-bold leading-tight   md:block"> Ganti Delay </h1>
          <div class="grid gap-2 grid-cols-1 text-center">
            <div>
              <h1 class="text-xs">Delay Sekarang</h1>
              <p class="font-bold text-lg ">{{alsData.delayALS.value}} mS</p>
            </div>

          </div>
          <Slider
              v-model="inputSlider"
              :max="500"
              :min="30"
              :step="10"
              class="w-4/5 mt-4"
          />
        </div>

      </section>
    </main>
    <footer class="py-6 md:px-8 md:py-0">
      <div class="container flex flex-col items-center justify-between gap-4 md:h-24 md:flex-row">
        <div class="text-center text-sm leading-loose text-muted-foreground md:text-left"><span class="inline-block">
          Built and designed by <a
            href="#" target=""
            class="underline underline-offset-4 font-bold decoration-foreground"> workalogi </a></span>
          <br>

        </div>
      </div>
    </footer>
  </div>
</template>

<style scoped>
html {
  font-family: "Verdana", "Arial", sans-serif;
  display: inline-block;
  margin: 0px auto;
  text-align: center;
}
.button {
  background-color: #4CAF50;
  border: none;
  color: white;
  padding: 16px 40px;
  border-radius: 10px;
  text-decoration: none;
  font-size: 30px;
  margin: 2px;
  cursor: pointer;
}
.button2 {
  background-color: #555555;
  border-radius: 10px;
}
</style>
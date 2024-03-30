<script setup lang="ts">
import {
  ArrowUpRight,
  Users,
  Siren,
  TimerReset
} from 'lucide-vue-next'
import {AspectRatio} from '@/components/ui/aspect-ratio'
import {Button} from '@/components/ui/button'
import {Card, CardContent, CardFooter, CardHeader, CardTitle} from '@/components/ui/card'
import {ref} from 'vue'
import {Minus, Plus} from 'lucide-vue-next'
import MainHeader from "@/components/content/MainHeader.vue";
import {
  Drawer,
  DrawerClose,
  DrawerContent,
  DrawerDescription,
  DrawerFooter,
  DrawerHeader,
  DrawerTitle,
  DrawerTrigger,
} from '@/components/ui/drawer'

import {Label} from '@/components/ui/label'

import {RadioGroup, RadioGroupItem} from '@/components/ui/radio-group'
import { Textarea } from '@/components/ui/textarea'
const mode = [
  {value: 'mode1', name: 'MODE 1'},
  {value: 'mode2', name: 'MODE 2'},
  {value: 'mode3', name: 'MODE 3'},
  {value: 'mode4', name: 'MODE 4'},
  {value: 'mode5', name: 'MODE 5'},
  {value: 'mode6', name: 'MODE 6'},
  {value: 'mode7', name: 'MODE 7'},
  {value: 'mode8', name: 'MODE 8'},
  {value: 'mode9', name: 'MODE 9'},
  {value: 'modeON', name: 'MODE ON'},
  {value: 'modeOFF', name: 'MODE OFF'},

]
const delayNow = ref(350)
const modeNow = ref('mode7');
const deviceNow = ref('ROKKY JR');

function findModeNameByValue(value) {
  const foundMode = mode.find(item => item.value === value);
  return foundMode ? foundMode.name : null;
}
</script>

<template>
  <div class="flex min-h-screen w-full flex-col">
    <MainHeader></MainHeader>

    <main class="flex flex-1 flex-col gap-3 p-4 md:gap-3 md:p-8">
      <div class="grid gap-4 md:grid-cols-1 md:gap-8 lg:grid-cols-1">
<!--        <Card>-->
<!--          <CardHeader class="flex flex-row items-center justify-between space-y-2 pb-2">-->
<!--            <CardTitle class="text-md font-medium">-->
<!--              Welcome, ROCKY JR- -->
<!--            </CardTitle>-->
<!--            <Users class="h-4 w-4 text-muted-foreground"/>-->
<!--          </CardHeader>-->
<!--          <CardContent>-->
<!--            <div class="my-2">-->
<!--              <AspectRatio :ratio="16 / 9" class="bg-muted">-->
<!--                <img-->
<!--                    src="https://images.unsplash.com/photo-1588345921523-c2dcdb7f1dcd?w=800&dpr=2&q=80"-->
<!--                    alt="Photo by Drew Beamer"-->
<!--                    class="rounded-md object-cover w-full h-full"-->
<!--                >-->
<!--              </AspectRatio>-->
<!--            </div>-->

<!--          </CardContent>-->
<!--          <CardFooter class="border-t px-6 py-4 w-full">-->
<!--            <Button>-->
<!--              Ganti Foto, ROCKKY JR- -->
<!--              <ArrowUpRight class="ml-2 h-4 w-4"/>-->
<!--            </Button>-->
<!--          </CardFooter>-->
<!--        </Card>-->
        <Card>
          <CardHeader class="flex flex-row items-center justify-between space-y-2 pb-2">
            <CardTitle class="text-md font-medium">
              Informasi Sistem
            </CardTitle>
            <Users class="h-4 w-4 text-muted-foreground"/>
          </CardHeader>
          <CardContent>
            <div class="my-2">
              <p class="text-xs text-muted-foreground">
                Nama
              </p>
              <div class="text-2xl font-bold">
                {{deviceNow}}
              </div>
            </div>
            <div class="my-2">
              <p class="text-xs text-muted-foreground">
                Serial/Nomor-Seri
              </p>
              <div class="text-2xl font-bold">
                ALS21295123#212
              </div>
            </div>

          </CardContent>
          <CardFooter class="border-t px-6 py-4 w-full">
            <Drawer>
              <DrawerTrigger as-child>
                <Button>
                  Ganti Informasi Sistem
                  <ArrowUpRight class="ml-2 h-4 w-4"/>
                </Button>
              </DrawerTrigger>
              <DrawerContent>
                <div class="mx-auto w-full max-w-sm">
                  <DrawerHeader>
                    <DrawerTitle class="text-2xl"> Ganti Informasi Sistem</DrawerTitle>
                    <DrawerDescription>Ganti Informasi Auto Light System Anda</DrawerDescription>
                  </DrawerHeader>
                  <div class="p-4 pb-0">
                    <div class="flex items-center justify-center space-x-2">

                      <div class="flex-1 text-center">
                        <div class=" font-bold tracking-tighter">
                          <Textarea placeholder="Isikan Informasi Auto Light System Baru" v-model="deviceNow"/>
                        </div>

                      </div>

                    </div>
                    <div class="my-3 px-3 text-center h-auto">
                      <hr class="my-2">
                      <div class="text-[0.70rem] uppercase text-muted-foreground">
                        Ketika Anda Menyimpan, Sistem akan restart, kemudian mengganti SSID/Nama Wifi Anda
                      </div>
                    </div>
                  </div>
                  <DrawerFooter>
                    <Button @click="">Simpan</Button>
                    <DrawerClose as-child>
                      <Button variant="outline">
                        Cancel
                      </Button>
                    </DrawerClose>
                  </DrawerFooter>
                </div>
              </DrawerContent>
            </Drawer>

          </CardFooter>
        </Card>
        <Card>
          <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle class="text-md font-medium">
              Status Auto Light System
            </CardTitle>
            <Siren class="h-6 w-6 text-muted-foreground"/>
          </CardHeader>
          <CardContent>
            <div class="py-2">
              <p class="text-xs text-muted-foreground">
                Mode Sedeang Berjalan
              </p>
              <div class="text-2xl font-bold">
                {{ findModeNameByValue(modeNow) }}
              </div>
            </div>
          </CardContent>
          <CardFooter class="border-t px-6 py-4 w-full">
            <Drawer>
              <DrawerTrigger as-child>
                <Button>
                  Ganti Mode
                  <ArrowUpRight class="ml-2 h-4 w-4"/>
                </Button>
              </DrawerTrigger>
              <DrawerContent>
                <div class="mx-auto w-full max-w-sm">
                  <DrawerHeader>
                    <DrawerTitle>Ganti Mode Lampu</DrawerTitle>
                    <DrawerDescription>Pilih Mode Lampu Auto Light System</DrawerDescription>
                  </DrawerHeader>
                  <div class="p-4 pb-0">
                    <div class="flex items-center justify-center space-x-2">
                      <div class="flex-1 text-center">
                        <div class="text-6xl font-bold tracking-tighter">
                          {{findModeNameByValue(modeNow)}}
                        </div>
                        <div class="text-[0.70rem] uppercase text-muted-foreground">
                          Mode Sekarang
                        </div>
                      </div>
                    </div>

                    <div class="my-2 px-3 h-auto">
                      <hr>
                      <RadioGroup v-model="modeNow" class="grid mt-2 py-2 grid-cols-2 gap-4">
                        <template v-for="item in mode" :key="item.value">
                          <div>
                            <RadioGroupItem :id="item.value" :value="item.value" class="peer sr-only"/>
                            <Label
                                :for="item.value"
                                :class="[
                                  'flex flex-col items-center justify-between rounded-md border-2 border-muted bg-popover p-4 hover:bg-accent hover:text-accent-foreground',
                                  {'peer-data-[state=checked]:border-primary': true, '[&:has([data-state=checked])]:border-primary': true}
                                ]"
                            >
                              <Siren class="h-6 w-6 text-muted-foreground"/>
                              {{ item.name }}
                            </Label>
                          </div>
                        </template>

                      </RadioGroup>
                    </div>
                  </div>
                  <DrawerFooter>
                    <Button>Submit</Button>
                    <DrawerClose as-child>
                      <Button variant="outline">
                        Cancel
                      </Button>
                    </DrawerClose>
                  </DrawerFooter>
                </div>
              </DrawerContent>
            </Drawer>
          </CardFooter>
        </Card>
        <Card>
          <CardHeader class="flex flex-row items-center justify-between space-y-0 pb-2">
            <CardTitle class="text-md font-medium">
              Delay Auto Light System
            </CardTitle>
            <TimerReset class="h-6 w-6 text-muted-foreground"/>
          </CardHeader>
          <CardContent>
            <div class="my-2">
              <p class="text-xs text-muted-foreground">
                Delay Hidup-Mati Sistem
              </p>
              <div class="text-2xl font-bold">
                {{ delayNow/1000 }} Detik
              </div>
            </div>
          </CardContent>
          <CardFooter class="border-t px-6 py-4 w-full">
            <Drawer>
              <DrawerTrigger as-child>
                <Button>
                  Ganti Delay
                  <ArrowUpRight class="ml-2 h-4 w-4"/>
                </Button>
              </DrawerTrigger>
              <DrawerContent>
                <div class="mx-auto w-full max-w-sm">
                  <DrawerHeader>
                    <DrawerTitle class="text-2xl">Ganti Nilai Delay</DrawerTitle>
                    <DrawerDescription>Ubah nilai waktu jeda Hidup-Mati sistem Auto Light</DrawerDescription>
                  </DrawerHeader>
                  <div class="p-4 pb-0">
                    <div class="flex items-center justify-center space-x-2">
                      <Button
                          variant="outline"
                          size="icon"
                          class="h-8 w-8 shrink-0 rounded-full"
                          :disabled="delayNow <= 30"
                          @click="delayNow -= 10"
                      >
                        <Minus class="h-4 w-4"/>
                        <span class="sr-only">Decrease</span>
                      </Button>
                      <div class="flex-1 text-center">
                        <div class="text-7xl font-bold tracking-tighter">
                          {{ delayNow }}
                        </div>
                        <div class="text-[0.70rem] uppercase text-muted-foreground">
                          Satuan Mili Detik (Mili Sekon)
                        </div>
                      </div>
                      <Button
                          variant="outline"
                          size="icon"
                          class="h-8 w-8 shrink-0 rounded-full"
                          :disabled="delayNow >= 1000"
                          @click="delayNow += 10"
                      >
                        <Plus class="h-4 w-4"/>
                        <span class="sr-only">Increase</span>
                      </Button>
                    </div>
                    <div class="my-3 px-3 h-[120px]">

                    </div>
                  </div>
                  <DrawerFooter>
                    <Button>Simpan</Button>
                    <DrawerClose as-child>
                      <Button variant="outline">
                        Cancel
                      </Button>
                    </DrawerClose>
                  </DrawerFooter>
                </div>
              </DrawerContent>
            </Drawer>
          </CardFooter>
        </Card>

      </div>

    </main>
    <footer class="py-6 md:px-8 md:py-0">
      <div class="container flex flex-col items-center justify-between gap-4 md:h-24 md:flex-row">
        <div class="text-center text-sm leading-loose text-muted-foreground md:text-left"><span class="inline-block">
          Built and designed by <a
            href="https://twitter.com/shadcn" target="_blank"
            class="underline underline-offset-4 font-bold decoration-foreground"> workalogi </a></span>
          <br>

        </div>
      </div>
    </footer>
  </div>
</template>

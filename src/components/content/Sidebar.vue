<script setup lang="ts">
import { AlertCircle } from 'lucide-vue-next'
import {Card, CardContent, CardDescription, CardHeader, CardTitle} from '@/components/ui/card'
import { Alert, AlertDescription, AlertTitle } from '@/components/ui/alert'
import {Sheet, SheetContent, SheetTrigger} from "@/components/ui/sheet";
import {Button} from "@/components/ui/button";
import {Menu} from "lucide-vue-next";
</script>

<template>
  <Sheet>
    <SheetTrigger as-child>
      <Button
          variant="outline"
          size="icon"
          class="shrink-0 md:hidden"
      >
        <Menu class="h-5 w-5"/>
        <span class="sr-only">Toggle navigation menu</span>
      </Button>
    </SheetTrigger>
    <SheetContent side="left" class="flex flex-col">
      <nav class="grid gap-6 mt-5 text-lg font-medium">
        <div class="mt-auto p-2">
          <Card>
            <CardHeader class="p-5  md:p-4">
              <CardTitle>Upgrade to App</CardTitle>
              <CardDescription class="py-2">
                Unlock all features and get unlimited access to our support
                team.
                <Alert class="mt-2" >
                  <AlertCircle class="w-4 h-4" />
                  <AlertTitle>Informasi</AlertTitle>
                  <AlertDescription>
                    Sudah versi Terbaru
                  </AlertDescription>
                </Alert>
              </CardDescription>
            </CardHeader>
            <CardContent class="md:p-4 md:pt-2">
              <Button size="sm"  variant="outline" class="my-2 w-full">
                Check
              </Button>
              <Button size="sm" class="my-2 w-full">
                Upgrade
              </Button>
            </CardContent>
          </Card>
        </div>
        <div class="mt-auto p-2">
          <Card>
            <CardHeader class="p-5  md:p-4">
              <CardTitle>Upgrade to Firmware</CardTitle>
              <CardDescription class="py-2">
                Unlock all features and get unlimited access to our support
                team.
                <Alert class="mt-2" >
                  <AlertCircle class="w-4 h-4" />
                  <AlertTitle>Informasi</AlertTitle>
                  <AlertDescription>
                    Sudah versi Terbaru
                  </AlertDescription>
                </Alert>
              </CardDescription>
            </CardHeader>
            <CardContent class="  md:p-4 md:pt-2">
              <Button size="sm"  variant="outline" class="my-2 w-full">
                Check
              </Button>
              <Button size="sm" class="my-2 w-full">
                Upgrade
              </Button>
            </CardContent>
          </Card>
        </div>
      </nav>


    </SheetContent>
  </Sheet>
</template>

<style scoped>

</style>
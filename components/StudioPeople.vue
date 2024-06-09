<script setup lang="ts">
import { Mic, MicOff, Menu } from 'lucide-vue-next'
import DropdownMenu from './ui/dropdown-menu/DropdownMenu.vue';
</script>

<template>
  <div class="grid sm:grid-cols-1 md:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-2 p-2">
    <Card class="p-2 h-36">
      <CardHeader class="flex flex-row">
        <img class="h-10 w-10 rounded-full" src="https://avatars.githubusercontent.com/u/78635021?v=4" />
        <span class="text-xl text-wrap mx-3">Acbox Liu</span>
      </CardHeader>
      <CardContent>
        <Button class="w-10 h-10 hover:bg-gray-100 border float-right">
          <Mic class="fixed w-3 h-3" />
        </Button>
        <div class="float-right">
          <DropdownMenu>
            <DropdownMenuTrigger as-child>
              <Button class="w-10 h-10 hover:bg-gray-100 border">
                <Menu class="fixed w-3 h-3" />
              </Button>
            </DropdownMenuTrigger>
            <DropdownMenuContent>
              <DropdownMenuLabel>
                Options
              </DropdownMenuLabel>
              <DropdownMenuItem>+ Add to friends</DropdownMenuItem>
              <DropdownMenuSeparator />
              <DropdownMenuGroup>
                <DropdownMenuItem>Remove</DropdownMenuItem>
                <DropdownMenuItem>Close Mic</DropdownMenuItem>
              </DropdownMenuGroup>
              <DropdownMenuSeparator />
              <DropdownMenuItem>Get more</DropdownMenuItem>
            </DropdownMenuContent>
          </DropdownMenu>
        </div>
      </CardContent>
    </Card>
  </div>
</template>
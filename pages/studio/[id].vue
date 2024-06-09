<template>
  <div class="grid h-screen w-full pl-[53px]">
    <aside class="inset-y fixed  left-0 z-20 flex h-full flex-col border-r">
      <div class="border-b p-2">
        <Button variant="outline" size="icon" aria-label="Home">
          <Triangle class="size-5 fill-foreground" />
        </Button>
      </div>
      <nav class="grid gap-1 p-2">
        <TooltipProvider class="hover:bg-gray-100" @click="current = 'people'">
          <Tooltip>
            <TooltipTrigger as-child>
              <Button variant="ghost" size="icon" class="rounded-lg bg-muted" aria-label="Playground">
                <Users class="size-5" />
              </Button>
            </TooltipTrigger>
          </Tooltip>
        </TooltipProvider>
        <TooltipProvider class="hover:bg-gray-100" @click="current = 'console'">
          <Tooltip>
            <TooltipTrigger as-child>
              <Button variant="ghost" size="icon" class="rounded-lg bg-muted" aria-label="Playground">
                <SquareTerminal class="size-5" />
              </Button>
            </TooltipTrigger>
          </Tooltip>
        </TooltipProvider>
      </nav>
    </aside>
    <main class="m-10 mt-5">
      <StudioPeople v-if="current === 'people'"/>
      <StudioConsole v-else-if="current === 'console'"/>
      <StudioBottomConsole class="fixed bottom-0 left-[56px]"/>
    </main>
  </div>
</template>

<script setup lang="ts">
import { SquareTerminal, Triangle, Users } from 'lucide-vue-next'

const current: Ref<'people' | 'console'> = ref('people')
</script>

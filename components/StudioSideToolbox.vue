<template>
  <aside class="inset-y fixed  left-0 z-20 flex h-full flex-col border-r">
    <div class="border-b p-2">
      <Button variant="outline" size="icon" aria-label="Home">
        <Triangle class="size-5 fill-foreground" />
      </Button>
    </div>
    <nav class="grid gap-1 p-2">
      <nuxt-link :to="`/studio/${id}/people`">
        <TooltipProvider class="hover:bg-gray-100">
          <Tooltip>
            <TooltipTrigger as-child>
              <Button variant="ghost" size="icon" class="rounded-lg bg-muted" aria-label="Playground">
                <Users class="size-5" />
              </Button>
            </TooltipTrigger>
          </Tooltip>
        </TooltipProvider>
      </nuxt-link>
      <nuxt-link :to="`/studio/${id}/console`">
        <TooltipProvider class="hover:bg-gray-100">
          <Tooltip>
            <TooltipTrigger as-child>
              <Button variant="ghost" size="icon" class="rounded-lg bg-muted" aria-label="Playground">
                <SquareTerminal class="size-5" />
              </Button>
            </TooltipTrigger>
          </Tooltip>
        </TooltipProvider>
      </nuxt-link>
    </nav>
  </aside>
</template>

<script setup lang="ts">
import { SquareTerminal, Triangle, Users } from 'lucide-vue-next'

const route = useRoute()
const id = route.params.id
</script>
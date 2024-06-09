<template>
  <div class="relative min-h-screen w-full md:grid md:grid-cols-[220px_1fr] lg:grid-cols-[280px_1fr]">
    <div :class="{ 'translate-x-0': isSidebarOpen, '-translate-x-full': !isSidebarOpen }"
      class="fixed inset-y-0 left-0 z-50 w-64 transform bg-white transition-transform duration-300 md:relative md:translate-x-0 md:w-auto md:border-r">
      <div class="flex h-full max-h-screen flex-col gap-2">
        <div class="flex-1">
          <nav class="grid items-start text-sm font-medium lg:px-4">
            <a href="#" @click="input?.scrollIntoView({ behavior: 'smooth' })"
              class="flex items-center gap-3 rounded-lg px-3 py-2 text-muted-foreground transition-all hover:text-primary">
              <Mic class="h-4 w-4" />
              Voice Input
            </a>
            <a href="#" @click="output?.scrollIntoView({ behavior: 'smooth' })"
              class="flex items-center gap-3 rounded-lg px-3 py-2 text-muted-foreground transition-all hover:text-primary">
              <Speaker class="h-4 w-4" />
              Voice Output
            </a>
            <a href="#" @click="rule?.scrollIntoView({ behavior: 'smooth' })"
              class="flex items-center gap-3 rounded-lg bg-muted px-3 py-2 text-primary transition-all hover:text-primary">
              <Book class="h-4 w-4" />
              Rule
            </a>
            <a href="#" @click="options?.scrollIntoView({ behavior: 'smooth' })"
              class="flex items-center gap-3 rounded-lg px-3 py-2 text-muted-foreground transition-all hover:text-primary">
              <CircleAlert class="h-4 w-4" />
              <span class="text-red-500">
                Dangerous Options
              </span>
            </a>
          </nav>
        </div>
      </div>
    </div>

    <div v-if="isSidebarOpen" @click="closeSidebar" class="fixed inset-0 z-40 bg-black bg-opacity-50 md:hidden"></div>

    <main class="m-5">
      <h1 class="text-2xl pt-5">Voice Input</h1>
      <div class="my-5 flex flex-grow flex-row" ref="input">
        <NumberField id="age" :default-value="100" :min="0" :max="100" class="w-36">
          <NumberFieldContent>
            <NumberFieldDecrement />
            <NumberFieldInput />
            <NumberFieldIncrement />
          </NumberFieldContent>
        </NumberField>
      </div>
      <hr />
      <h1 class="text-2xl pt-5" ref="output">Voice Output</h1>
      <div class="my-28"></div>
      <hr />
      <h1 class="text-2xl pt-5" ref="rule">Rule</h1>
      <div class="my-28"></div>
      <hr />
      <h1 class="text-2xl pt-5" ref="options">Dangerous Options</h1>
      <div class="my-5">
        <Card class="w-full">
          <CardContent class="h-44">
            <div class="flex flex-col">
              <div class="float-left px-3 py-3">
                <h2>
                  <strong>Transfer</strong>
                </h2>
                <span>Transfer the admin to others</span>
                <div class="float-right">
                  <Button class="border hover:bg-gray-100">transfer</Button>
                </div>
              </div>
            </div>
            <hr />
            <div>
              <div class="float-left px-3 py-3">
                <h2>
                  <strong>Delete</strong>
                </h2>
                <span>Delete this room</span>
              </div>
              <div class="float-right px-3 py-5">
                <Button class="border hover:bg-gray-100">delete</Button>
              </div>
            </div>
            <hr />
          </CardContent>
        </Card>
      </div>
      <hr />
    </main>
  </div>
</template>

<script setup lang="ts">
import {
  Mic,
  Book,
  Speaker,
  CircleAlert,
} from 'lucide-vue-next'

const isSidebarOpen = ref(false);

function closeSidebar() {
  isSidebarOpen.value = false;
}
const input = ref<HTMLElement | null>(null)
const output = ref<HTMLElement | null>(null)
const rule = ref<HTMLElement | null>(null)
const options = ref<HTMLElement | null>(null)

const inputVoice = ref<[number]>([100])
</script>

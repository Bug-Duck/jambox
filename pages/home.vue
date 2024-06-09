<template>
  <div class="relative min-h-screen w-full md:grid md:grid-cols-[220px_1fr] lg:grid-cols-[280px_1fr]">
    <!-- Mobile Menu Button -->
    <div class="fixed top-0 left-0 p-4 md:hidden">
      <Button @click="toggleSidebar" v-if="!isSidebarOpen" variant="outline" size="icon" class="h-8 w-8">
        <Menu class="h-4 w-4" />
        <span class="sr-only">Toggle menu</span>
      </Button>
    </div>

    <!-- Sidebar -->
    <div :class="{'translate-x-0': isSidebarOpen, '-translate-x-full': !isSidebarOpen}" class="fixed inset-y-0 left-0 z-50 w-64 transform bg-white transition-transform duration-300 md:relative md:translate-x-0 md:w-auto md:border-r">
      <div class="flex h-full max-h-screen flex-col gap-2">
        <div class="flex h-14 items-center border-b px-4 lg:h-[60px] lg:px-6">
          <a href="/" class="flex items-center gap-2 font-semibold">
            <Package2 class="h-6 w-6" />
            <span>Jambox</span>
          </a>
          <Button variant="outline" size="icon" class="ml-auto h-8 w-8">
            <Bell class="h-4 w-4" />
            <span class="sr-only">Toggle notifications</span>
          </Button>
        </div>
        <div class="flex-1">
          <nav class="grid items-start px-2 text-sm font-medium lg:px-4">
            <a
              href="#"
              class="flex items-center gap-3 rounded-lg px-3 py-2 text-muted-foreground transition-all hover:text-primary"
              @click="setCurrent('dashboard')"
            >
              <Home class="h-4 w-4" />
              Dashboard
            </a>
            <a
              href="#"
              class="flex items-center gap-3 rounded-lg px-3 py-2 text-muted-foreground transition-all hover:text-primary"
              @click="setCurrent('studios')"
            >
              <Videotape class="h-4 w-4" />
              Studios
              <Badge class="ml-auto flex h-6 w-6 shrink-0 items-center justify-center rounded-full">
                6
              </Badge>
            </a>
            <a
              href="#"
              class="flex items-center gap-3 rounded-lg bg-muted px-3 py-2 text-primary transition-all hover:text-primary"
              @click="setCurrent('recording')"
            >
              <Package class="h-4 w-4" />
              Recording
            </a>
            <a
              href="#"
              class="flex items-center gap-3 rounded-lg px-3 py-2 text-muted-foreground transition-all hover:text-primary"
              @click="setCurrent('friends')"
            >
              <Users class="h-4 w-4" />
              Friends
            </a>
          </nav>
        </div>
      </div>
    </div>

    <!-- Overlay -->
    <div v-if="isSidebarOpen" @click="closeSidebar" class="fixed inset-0 z-40 bg-black bg-opacity-50 md:hidden"></div>

    <!-- Main Content -->
    <div class="flex flex-col">
      <Dash v-if="current === 'dashboard'" />
      <Studios v-if="current === 'studios'" />
      <Recording v-if="current === 'recording'" />
      <Friends v-if="current === 'friends'" />
    </div>
  </div>
</template>

<script setup lang="ts">
import {
  Bell,
  Home,
  Menu,
  Package,
  Package2,
  Users,
  Videotape
} from 'lucide-vue-next'

import { ref } from 'vue';

const current = ref<'dashboard' | 'studios' | 'recording' | 'friends'>('dashboard');
const isSidebarOpen = ref(false);

function toggleSidebar() {
  isSidebarOpen.value = !isSidebarOpen.value;
}

function closeSidebar() {
  isSidebarOpen.value = false;
}

function setCurrent(view: 'dashboard' | 'studios' | 'recording' | 'friends') {
  current.value = view;
  if (window.innerWidth < 768) {
    isSidebarOpen.value = false;
  }
}
</script>

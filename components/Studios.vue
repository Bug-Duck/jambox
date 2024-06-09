<template>
  <div class="p-16">
    <span class="text-2xl font-thin select-none">Studios</span>
    <ul class="pt-6">
      <li v-for="info in infos" class="pb-3">
        <Card class="w-full h-28 justify-start hover:bg-gray-100">
          <CardHeader class="pb-1">{{ info.name }}</CardHeader>
          <CardDescription class="pl-6">{{ info.currentMember }} / {{ info.maxMember }}</CardDescription>
        </Card>
      </li>
      <li>
        <Card class="w-full h-6 text-center hover:bg-gray-100 select-none">
          +
        </Card>
      </li>
    </ul>
  </div>
</template>

<script setup lang="ts">
interface StudioInfo {
  name: string,
  id: string,
  maxMember: number,
  currentMember: number
}

const studios: StudioInfo[] = [
  {
    name: 'Test1',
    id: '1',
    maxMember: 10,
    currentMember: 3
  }
]

const infos = ref(studios)
</script>
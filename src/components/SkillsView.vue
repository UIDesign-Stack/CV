<script setup>
import ProfileCard from './ProfileCard.vue'
import { ChartBarIcon, AcademicCapIcon } from '@heroicons/vue/24/outline'

const skillGroups = [
  {
    category: 'UI / UX',
    tools: [
      { name: 'Figma', color: 'bg-gray-900', text: 'F' },
      { name: 'Adobe XD', color: 'bg-pink-600', text: 'Xd' },
    ],
  },
  {
    category: 'Web Programmer',
    tools: [
      { name: 'Laravel', color: 'bg-red-600', text: 'La' },
      { name: 'JavaScript', color: 'bg-yellow-400', text: 'JS', dark: true },
      { name: 'HTML', color: 'bg-orange-600', text: 'H' },
      { name: 'CSS', color: 'bg-blue-600', text: 'C' },
    ],
  },
  {
    category: 'Graphic Design',
    tools: [
      { name: 'CorelDRAW', color: 'bg-green-700', text: 'Cd' },
    ],
  },
  {
    category: '3D Modeling',
    tools: [
      { name: 'Google SketchUp', color: 'bg-blue-500', text: 'Su' },
      { name: 'Blender', color: 'bg-orange-500', text: 'Bl' },
    ],
  },
  {
    category: 'Video Editing',
    tools: [
      { name: 'Adobe Premiere Pro', color: 'bg-indigo-700', text: 'Pr' },
    ],
  },
  {
    category: 'Animasi',
    tools: [
      { name: 'Adobe After Effect', color: 'bg-purple-700', text: 'Ae' },
    ],
  },
  {
    category: 'Roblox Creator',
    tools: [
      { name: 'Roblox Studio', color: 'bg-gray-800', text: 'Rb' },
    ],
  },
]

const learning = [
  { name: 'Vue.js', color: 'bg-green-600', text: 'Vue' },
  { name: 'Tailwind CSS', color: 'bg-cyan-500', text: 'Tw' },
  { name: 'Python', color: 'bg-blue-700', text: 'Py' },
]
</script>

<template>
  <ProfileCard />

  <div class="md:col-start-2 md:col-end-4 md:row-start-2 bg-white rounded-2xl shadow-sm p-8">

    <div class="flex items-start justify-between mb-6">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded-xl bg-orange-100 flex items-center justify-center">
          <ChartBarIcon class="w-5 h-5 text-orange-500" />
        </div>
        <div>
          <h2 class="font-bold text-gray-900 text-xl">Skills</h2>
          <p class="text-sm text-gray-500">Kemampuan yang saya kuasai di berbagai bidang.</p>
        </div>
      </div>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <div
        v-for="group in skillGroups"
        :key="group.category"
        class="border border-gray-100 rounded-2xl p-5"
      >
        <h3 class="font-bold text-gray-900 mb-3">{{ group.category }}</h3>
        <div class="flex flex-wrap gap-2">
          <div
            v-for="tool in group.tools"
            :key="tool.name"
            class="flex items-center gap-2 bg-gray-50 rounded-xl pl-1.5 pr-3 py-1.5"
          >
            <span
              class="w-7 h-7 rounded-lg flex items-center justify-center text-xs font-bold"
              :class="[tool.color, tool.dark ? 'text-gray-900' : 'text-white']"
            >
              {{ tool.text }}
            </span>
            <span class="text-sm text-gray-700 font-medium">{{ tool.name }}</span>
          </div>
        </div>
      </div>
    </div>

    <div class="border-t border-gray-100 pt-6">
      <div class="flex items-center gap-3 mb-4">
        <div class="w-10 h-10 rounded-xl bg-orange-100 flex items-center justify-center">
          <AcademicCapIcon class="w-5 h-5 text-orange-500" />
        </div>
        <h3 class="font-bold text-gray-900">Sedang Dipelajari</h3>
      </div>
      <div class="flex flex-wrap gap-3">
        <div
          v-for="item in learning"
          :key="item.name"
          class="flex items-center gap-2 border border-gray-100 rounded-xl pl-1.5 pr-4 py-2"
        >
          <span
            class="w-8 h-8 rounded-lg flex items-center justify-center text-xs font-bold text-white"
            :class="item.color"
          >
            {{ item.text }}
          </span>
          <span class="text-sm text-gray-700 font-medium">{{ item.name }}</span>
        </div>
      </div>
    </div>

  </div>
</template>
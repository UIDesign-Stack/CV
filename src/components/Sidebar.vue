<script setup>
import {
  UserIcon,
  AcademicCapIcon,
  BriefcaseIcon,
  ChartBarIcon,
  FolderIcon,
  CheckBadgeIcon,
  EnvelopeIcon,
} from '@heroicons/vue/24/outline'

const props = defineProps(['activeMenu'])
const emit = defineEmits(['update:activeMenu'])

const menuItems = [
  { name: 'About Me', icon: UserIcon },
  { name: 'Education', icon: AcademicCapIcon },
  { name: 'Experience', icon: BriefcaseIcon },
  { name: 'Skills', icon: ChartBarIcon },
  { name: 'Portfolio', icon: FolderIcon },
  { name: 'Certificates', icon: CheckBadgeIcon },
  { name: 'Contact', icon: EnvelopeIcon },
]
</script>

<template>
  <aside class="md:col-start-1 md:row-start-1 md:row-span-2 bg-zinc-900/0 rounded-2xl shadow-sm p-6 flex flex-col items-center">

    <div class="relative w-36 h-36 mb-4">
      <div class="absolute inset-0 rounded-full bg-orange-500/10 translate-x-2 translate-y-2"></div>
      <img
        src="/me.jpeg"
        alt="Foto profil"
        class="relative w-36 h-36 rounded-full object-cover border-4 border-zinc-800 shadow"
      />
    </div>

    <h1 class="text-lg font-bold text-zinc-50">Chaerul Fajar Subhi</h1>
    <p class="text-sm text-orange-500 font-medium mb-6">Web Programmer & Graphic Designer</p>

    <nav class="w-full space-y-1 mb-6">
      <button
        v-for="item in menuItems"
        :key="item.name"
        @click="emit('update:activeMenu', item.name)"
        class="w-full flex items-center gap-3 px-4 py-3 rounded-xl text-left transition"
        :class="props.activeMenu === item.name
          ? 'bg-orange-500/15 text-orange-400 font-medium'
          : 'text-zinc-400 hover:bg-zinc-800'"
      >
        <component :is="item.icon" class="w-5 h-5" />
        <span>{{ item.name }}</span>
      </button>
    </nav>

    <div class="flex gap-3 mt-auto">
      <a href="#" class="w-10 h-10 rounded-full bg-zinc-800 flex items-center justify-center hover:bg-zinc-700 transition">
        <svg class="w-5 h-5 text-zinc-300" fill="currentColor" viewBox="0 0 24 24">
          <path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.207 11.387.6.113.793-.26.793-.577v-2.17c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.729.083-.729 1.205.084 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.42-1.305.763-1.605-2.665-.303-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.3 1.23a11.5 11.5 0 0 1 3.003-.404c1.02.005 2.047.138 3.003.404 2.29-1.552 3.297-1.23 3.297-1.23.653 1.652.24 2.873.118 3.176.77.84 1.233 1.91 1.233 3.22 0 4.61-2.805 5.624-5.478 5.92.43.372.823 1.104.823 2.226v3.3c0 .32.192.694.8.576C20.565 21.795 24 17.297 24 12c0-6.63-5.37-12-12-12z"/>
        </svg>
      </a>
      <a href="#" class="w-10 h-10 rounded-full bg-zinc-800 flex items-center justify-center hover:bg-zinc-700 transition">
        <svg class="w-5 h-5 text-zinc-300" fill="currentColor" viewBox="0 0 24 24">
          <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 1 1 0-4.125 2.062 2.062 0 0 1 0 4.125zM7.114 20.452H3.558V9h3.556v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/>
        </svg>
      </a>
      <a href="#" class="w-10 h-10 rounded-full bg-zinc-800 flex items-center justify-center hover:bg-zinc-700 transition">
        <svg class="w-5 h-5 text-zinc-300" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 1 0 0-18 9 9 0 0 0 0 18Z"/>
          <path stroke-linecap="round" stroke-linejoin="round" d="M3.6 9h16.8M3.6 15h16.8M12 3a15 15 0 0 1 4 9 15 15 0 0 1-4 9 15 15 0 0 1-4-9 15 15 0 0 1 4-9Z"/>
        </svg>
      </a>
    </div>

  </aside>
</template>
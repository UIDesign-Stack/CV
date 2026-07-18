<script setup>
import { inject } from 'vue'
import {
  UserIcon,
  CakeIcon,
  AcademicCapIcon,
  PlusCircleIcon,
  MapPinIcon,
} from '@heroicons/vue/24/outline'

const setActiveMenu = inject('setActiveMenu')
const cvUrl = `${import.meta.env.BASE_URL}CV.pdf`
</script>

<template>
  <div class="col-start-2 col-end-4 row-start-1 bg-white rounded-2xl shadow-sm p-8 flex gap-8">

    <!-- Kiri: Halo Saya -->
    <div class="flex-1">
      <p class="text-gray-500 mb-2">Halo! Saya 👋</p>
      <h1 class="text-4xl font-bold text-gray-900 mb-1">Chaerul Fajar Subhi</h1>
      <p class="text-orange-500 font-medium mb-4">Web Programmer & Graphic Designer</p>
      <p class="text-gray-500 leading-relaxed mb-6">
        Saya adalah seorang Web Programmer dan Graphic Designer dengan pengalaman
        dalam pengembangan website, desain grafis, serta dunia pendidikan.
        Saya senang belajar hal baru dan berkomitmen untuk memberikan hasil terbaik.
      </p>
      <div class="flex gap-3">
        <a
          :href="cvUrl"
          download
          class="bg-orange-500 hover:bg-orange-600 text-white px-5 py-3 rounded-xl font-medium flex items-center gap-2 transition"
        >
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M3 16.5v2.25A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75V16.5M16.5 12 12 16.5m0 0L7.5 12m4.5 4.5V3"/>
          </svg>
          Download CV
        </a>
        <button
          @click="setActiveMenu('Portfolio')"
          class="border border-gray-200 hover:bg-gray-50 text-gray-700 px-5 py-3 rounded-xl font-medium flex items-center gap-2 transition"
        >
          <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M7 17 17 7M7 7h10v10"/>
          </svg>
          Lihat Portfolio
        </button>
      </div>
    </div>

    <!-- Kanan: Info Pribadi -->
    <div class="w-80 border border-gray-100 rounded-2xl p-6 flex-shrink-0">
      <h2 class="font-bold text-gray-900 mb-4">Info Pribadi</h2>
      <ul class="space-y-4">
        <li class="flex items-center gap-3">
          <CakeIcon class="w-5 h-5 text-gray-400" />
          <div class="flex justify-between w-full text-sm">
            <span class="text-gray-500">Tanggal Lahir</span>
            <span class="text-gray-800 font-medium">29 November 1992</span>
          </div>
        </li>
        <li class="flex items-center gap-3">
          <UserIcon class="w-5 h-5 text-gray-400" />
          <div class="flex justify-between w-full text-sm">
            <span class="text-gray-500">Jenis Kelamin</span>
            <span class="text-gray-800 font-medium">Laki-laki</span>
          </div>
        </li>
        <li class="flex items-center gap-3">
          <AcademicCapIcon class="w-5 h-5 text-gray-400" />
          <div class="flex justify-between w-full text-sm">
            <span class="text-gray-500">Kebangsaan</span>
            <span class="text-gray-800 font-medium">Indonesia</span>
          </div>
        </li>
        <li class="flex items-center gap-3">
          <PlusCircleIcon class="w-5 h-5 text-gray-400" />
          <div class="flex justify-between w-full text-sm">
            <span class="text-gray-500">Agama</span>
            <span class="text-gray-800 font-medium">Islam</span>
          </div>
        </li>
        <li class="flex items-center gap-3">
          <MapPinIcon class="w-5 h-5 text-gray-400" />
          <div class="flex justify-between w-full text-sm">
            <span class="text-gray-500">Domisili</span>
            <span class="text-gray-800 font-medium">Bekasi, Jawa Barat</span>
          </div>
        </li>
      </ul>
    </div>

  </div>
</template>
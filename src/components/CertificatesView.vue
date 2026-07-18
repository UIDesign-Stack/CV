<script setup>
import ProfileCard from './ProfileCard.vue'
import { CheckBadgeIcon } from '@heroicons/vue/24/outline'

const certificates = [
  {
    title: 'Seminar Nasional Komputasi Masa Depan',
    subtitle: 'Windows 10, Hyper-V dan Azure',
    date: '02 April 2016',
  },
  {
    title: 'Menjadi Programmer Web',
    subtitle: 'Sebagai Pengisi Materi',
    date: '03 Desember 2016 - 07 Januari 2017',
  },
  {
    title: 'Seminar dan Workshop',
    subtitle: 'Oracle',
    date: '12 Maret 2016',
  },
  {
    title: 'Seminar',
    subtitle: 'E-Commerce',
    date: '13 Februari 2016',
  },
]
</script>

<template>
  <ProfileCard />

  <div class="md:col-start-2 md:col-end-4 md:row-start-2 bg-white rounded-2xl shadow-sm p-8">

    <div class="flex items-center gap-3 mb-6">
      <div class="w-10 h-10 rounded-xl bg-orange-100 flex items-center justify-center">
        <CheckBadgeIcon class="w-5 h-5 text-orange-500" />
      </div>
      <div>
        <h2 class="font-bold text-gray-900 text-xl">Certificates</h2>
        <p class="text-sm text-gray-500">Sertifikat dan penghargaan yang telah saya peroleh.</p>
      </div>
    </div>

    <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
      <div
        v-for="cert in certificates"
        :key="cert.title + cert.date"
        class="border border-gray-100 rounded-2xl p-5 flex items-start gap-4"
      >
        <div class="w-12 h-12 rounded-xl bg-orange-50 flex items-center justify-center flex-shrink-0">
          <svg class="w-6 h-6 text-orange-500" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75 11.25 15 15 9.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Z"/>
          </svg>
        </div>

        <div class="flex-1">
          <h3 class="font-bold text-gray-900">{{ cert.title }}</h3>
          <p class="text-orange-500 text-sm font-medium mt-0.5">{{ cert.subtitle }}</p>
          <div class="flex items-center gap-1.5 text-sm text-gray-500 mt-2">
            <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 21 7.5v11.25m-18 0A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75m-18 0v-7.5A2.25 2.25 0 0 1 5.25 9h13.5A2.25 2.25 0 0 1 21 11.25v7.5"/>
            </svg>
            {{ cert.date }}
          </div>
        </div>
      </div>
    </div>

  </div>
</template>
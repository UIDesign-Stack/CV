<script setup>
import ProfileCard from './ProfileCard.vue'
import { AcademicCapIcon } from '@heroicons/vue/24/outline'

const educations = [
  {
    school: 'STMIK PRANATA INDONESIA',
    major: 'S1 - Teknik Informatika',
    desc: 'Fokus pada pengembangan perangkat lunak, basis data, jaringan komputer, dan sistem informasi.',
    period: '2013 - 2017',
    status: 'Lulus 2017',
  },
  {
    school: 'SMAN 2 BABELAN',
    major: 'Ilmu Pengetahuan Alam (IPA)',
    desc: 'Angkatan Pertama',
    period: '2007 - 2010',
    status: 'Lulus 2010',
  },
  {
    school: 'SMPN 1 BABELAN',
    major: 'Sekolah Menengah Pertama',
    desc: '',
    period: '2004 - 2007',
    status: 'Lulus 2007',
  },
  {
    school: 'SDN KEBALEN 06',
    major: 'Sekolah Dasar',
    desc: '',
    period: '1998 - 2004',
    status: 'Lulus 2004',
  },
]
</script>

<template>
  <ProfileCard />

  <div class="md:col-start-2 md:col-end-4 md:row-start-2 bg-white rounded-2xl shadow-sm p-8">

    <div class="flex items-start justify-between mb-6 gap-4">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded-xl bg-orange-100 flex items-center justify-center">
          <AcademicCapIcon class="w-5 h-5 text-orange-500" />
        </div>
        <div>
          <h2 class="font-bold text-gray-900 text-xl">Education</h2>
          <p class="text-sm text-gray-500">Riwayat pendidikan formal yang telah saya tempuh.</p>
        </div>
      </div>

      <!-- Ikon dekoratif topi wisuda -->
      <svg class="hidden sm:block w-14 h-14 text-orange-400 opacity-70 flex-shrink-0" fill="none" viewBox="0 0 24 24">
        <path fill="currentColor" d="M12 3 1 8l11 5 9-4.09V17h2V8L12 3Z"/>
        <path fill="currentColor" d="M5 10.18v4.5L12 18l7-3.32v-4.5l-7 3.2-7-3.2Z" opacity="0.6"/>
      </svg>
    </div>

    <div class="relative pl-6 border-l-2 border-gray-100 space-y-4">
      <div
        v-for="edu in educations"
        :key="edu.school"
        class="relative"
      >
        <span class="absolute -left-[29px] top-6 w-3 h-3 rounded-full bg-orange-500 ring-4 ring-white"></span>

        <div class="border border-gray-100 rounded-2xl p-5 flex flex-col sm:flex-row sm:items-center gap-4">

          <!-- Ikon gedung (SVG custom) -->
          <div class="w-14 h-14 rounded-xl bg-orange-50 flex items-center justify-center flex-shrink-0">
            <svg class="w-7 h-7 text-orange-500" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3 21h18M4 21V8l8-5 8 5v13M9 21v-6h6v6M9 12h.01M15 12h.01M9 9h.01M15 9h.01"/>
            </svg>
          </div>

          <div class="flex-1">
            <h3 class="font-bold text-gray-900">{{ edu.school }}</h3>
            <p class="text-orange-500 text-sm font-medium">{{ edu.major }}</p>
            <p v-if="edu.desc" class="text-sm text-gray-500 mt-1">{{ edu.desc }}</p>
          </div>

          <div class="flex flex-row sm:flex-col items-center sm:items-end gap-2 sm:gap-2 flex-shrink-0 flex-wrap">
            <div class="flex items-center gap-1.5 text-sm text-gray-500">
              <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
                <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 21 7.5v11.25m-18 0A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75m-18 0v-7.5A2.25 2.25 0 0 1 5.25 9h13.5A2.25 2.25 0 0 1 21 11.25v7.5"/>
              </svg>
              {{ edu.period }}
            </div>
            <span class="inline-flex items-center gap-1 bg-green-50 text-green-600 text-xs font-medium px-3 py-1 rounded-full">
              <svg class="w-3.5 h-3.5" fill="currentColor" viewBox="0 0 20 20">
                <path fill-rule="evenodd" d="M16.7 5.3a1 1 0 0 1 0 1.4l-8 8a1 1 0 0 1-1.4 0l-4-4a1 1 0 1 1 1.4-1.4L8 12.6l7.3-7.3a1 1 0 0 1 1.4 0Z" clip-rule="evenodd"/>
              </svg>
              {{ edu.status }}
            </span>
          </div>

        </div>
      </div>
    </div>

  </div>
</template>
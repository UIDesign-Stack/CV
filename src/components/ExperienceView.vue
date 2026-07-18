<script setup>
import ProfileCard from './ProfileCard.vue'
import { BriefcaseIcon, MapPinIcon } from '@heroicons/vue/24/outline'

const experiences = [
  
  {
    company: 'SMK AL-BAHRI',
    role: 'Pengajar & Asesor',
    location: 'Indonesia',
    type: 'Part Time',
    desc: 'Tenaga Pendidik dan menjadi asesor kompetensi di jurusan Rekayasa Perangkat Lunak (RPL).',
    logoType: 'text',
    logoText: 'AB',
    logoBg: 'bg-blue-700',
  },
  {
    company: 'Start Up Nusantara Digital',
    role: 'Designer',
    location: 'Indonesia',
    type: 'Full Time',
    desc: 'Bertanggung jawab dalam pembuatan desain visual Seperti Logo, 3D Modeling, UI/UX',
    logoType: 'chart',
  },
  {
    company: 'HJ KARPET',
    role: 'Designer',
    location: 'Indonesia',
    type: 'Full Time',
    desc: 'Bertanggung jawab dalam pembutan Design Karpet.',
    logoType: 'text',
    logoText: 'HJ',
    logoBg: 'bg-green-900',
  },
  {
    company: 'Freelancer',
    role: 'Web Programmer, Design & Game Creator (Roblox)',
    location: 'Indonesia',
    type: 'Freelance',
    desc: 'Mengerjakan proyek secara freelance meliputi pembuatan website, desain grafis, dan pembuatan game di platform Roblox.',
    logoType: 'user',
    logoBg: 'bg-indigo-500',
  },
]
</script>

<template>
  <ProfileCard />

  <div class="md:col-start-2 md:col-end-4 md:row-start-2 bg-white rounded-2xl shadow-sm p-8">

    <div class="flex items-start justify-between mb-6 gap-4">
      <div class="flex items-center gap-3">
        <div class="w-10 h-10 rounded-xl bg-orange-100 flex items-center justify-center">
          <BriefcaseIcon class="w-5 h-5 text-orange-500" />
        </div>
        <div>
          <h2 class="font-bold text-gray-900 text-xl">Experience</h2>
          <p class="text-sm text-gray-500">Pengalaman kerja profesional yang telah saya jalani.</p>
        </div>
      </div>

      <!-- Ikon dekoratif tas kerja -->
      <svg class="hidden sm:block w-14 h-14 text-gray-500 opacity-70 flex-shrink-0" fill="none" viewBox="0 0 24 24">
        <path fill="currentColor" d="M9 6V4.5A1.5 1.5 0 0 1 10.5 3h3A1.5 1.5 0 0 1 15 4.5V6h4a2 2 0 0 1 2 2v3H3V8a2 2 0 0 1 2-2h4Zm2-1.5V6h2V4.5h-2Z"/>
        <path fill="currentColor" opacity="0.7" d="M3 12h18v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2v-6Z"/>
      </svg>
    </div>

    <div class="relative pl-6 border-l-2 border-gray-100 space-y-4">
      <div
        v-for="exp in experiences"
        :key="exp.company"
        class="relative"
      >
        <span class="absolute -left-[29px] top-6 w-3 h-3 rounded-full bg-orange-500 ring-4 ring-white"></span>

        <div class="border border-gray-100 rounded-2xl p-5 flex flex-col sm:flex-row sm:items-start gap-4">

          <!-- Logo perusahaan -->
          <div
            class="w-14 h-14 mx-auto sm:mx-0 rounded-xl flex items-center justify-center flex-shrink-0"
            :class="exp.logoBg || 'bg-gray-50 border border-gray-100'"
          >
            <!-- Chart icon -->
            <svg v-if="exp.logoType === 'chart'" class="w-7 h-7 text-blue-600" fill="none" stroke="currentColor" stroke-width="2" viewBox="0 0 24 24">
              <path stroke-linecap="round" stroke-linejoin="round" d="M3 17l6-6 4 4 8-8M21 7v4M21 7h-4"/>
            </svg>

            <!-- Text logo (HJ Karpet) -->
            <span v-else-if="exp.logoType === 'text'" class="text-white font-bold text-lg">
              {{ exp.logoText }}
            </span>

            <!-- User icon (Freelancer) -->
            <svg v-else-if="exp.logoType === 'user'" class="w-7 h-7 text-white" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 12a5 5 0 1 0 0-10 5 5 0 0 0 0 10Zm0 2c-4.4 0-8 2.2-8 5v2h16v-2c0-2.8-3.6-5-8-5Z"/>
            </svg>
          </div>

          <div class="flex-1">
            <h3 class="font-bold text-gray-900">{{ exp.company }}</h3>
            <p class="text-orange-500 text-sm font-medium mb-1">{{ exp.role }}</p>
            <div class="flex items-center gap-4 text-sm text-gray-500 mb-2">
              <span class="flex items-center gap-1.5">
                <svg class="w-4 h-4" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24">
                  <path stroke-linecap="round" stroke-linejoin="round" d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 21 7.5v11.25m-18 0A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75m-18 0v-7.5A2.25 2.25 0 0 1 5.25 9h13.5A2.25 2.25 0 0 1 21 11.25v7.5"/>
                </svg>
                {{ exp.period }}
              </span>
              <span class="flex items-center gap-1.5">
                <MapPinIcon class="w-4 h-4" />
                {{ exp.location }}
              </span>
            </div>
            <p class="text-sm text-gray-500">{{ exp.desc }}</p>
          </div>

          <span class="inline-flex items-center gap-1.5 bg-green-50 text-green-600 text-xs font-medium px-3 py-1.5 rounded-full flex-shrink-0 self-start sm:self-auto w-fit">
            <BriefcaseIcon class="w-3.5 h-3.5" />
            {{ exp.type }}
          </span>

        </div>
      </div>
    </div>

  </div>
</template>
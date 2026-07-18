<script setup>
import { BriefcaseIcon, ChartBarIcon, GlobeAltIcon } from '@heroicons/vue/24/outline'

const experiences = [
  { period: '2026 - Sekarang', title: 'Pengajar', place: 'SMK BM3', desc: 'Sebagai tenaga pengajar di jurusan Rekayasa Perangkat Lunak.' },
  { period: '2018 - 2025', title: 'Pengajar & Asesor', place: 'SMK AL-BAHRI', desc: 'Sebagai tenaga pendidik dan menjadi asesor di SMK AL-BAHRI.' },
  { period: '2017 - 2017', title: 'Web Programmer & Graphic Designer', place: 'Nusantara Digital', desc: 'Bergabung dalam dunia start-up sebagai Web Programmer dan Graphic Designer.' },
  { period: '2015 - 2015', title: 'Graphic Designer', place: 'HJ.Karpet', desc: 'Bergabung di perusahaan HJ Karpet sebagai Graphic Designer.' },
]

const skills = [
  { name: 'UI / UX', value: 90 },
  { name: 'Web Programmer', value: 90 },
  { name: 'Graphic Design', value: 85 },
  { name: 'Laravel', value: 90 },
  { name: 'PHP', value: 85 },
  { name: 'JavaScript', value: 75 },
  { name: 'MySQL', value: 80 },
  { name: 'HTML / CSS', value: 90 },
]

const languages = [
  { name: 'Indonesia', level: 5 },
  { name: 'English', level: 4 },
  { name: 'Arab', level: 2 },
]
</script>

<template>
  <div class="md:col-start-2 md:col-end-4 md:row-start-2 bg-zinc-900/0 rounded-2xl shadow-sm flex flex-col md:flex-row">

    <!-- Kiri: Pengalaman Kerja -->
    <div class="flex-1 p-8">
      <div class="flex items-center gap-3 mb-6">
        <div class="w-10 h-10 rounded-xl bg-orange-500/10 flex items-center justify-center">
          <BriefcaseIcon class="w-5 h-5 text-orange-500" />
        </div>
        <h2 class="font-bold text-zinc-50">Pengalaman Kerja</h2>
      </div>

      <div class="relative pl-6 border-l-2 border-zinc-800 space-y-8">
        <div v-for="exp in experiences" :key="exp.title + exp.period" class="relative">
          <span class="absolute -left-[29px] top-1 w-3 h-3 rounded-full bg-orange-500 ring-4 ring-white"></span>
          <p class="text-orange-500 text-sm font-medium mb-1">{{ exp.period }}</p>
          <h3 class="font-bold text-zinc-50">{{ exp.title }}</h3>
          <p class="text-sm text-zinc-400 mb-1">{{ exp.place }}</p>
          <p class="text-sm text-zinc-400">{{ exp.desc }}</p>
        </div>
      </div>
    </div>

    <!-- Kanan: Skills + Bahasa -->
    <div class="w-full md:w-96 border-t md:border-t-0 md:border-l border-zinc-800 p-6 flex-shrink-0">

      <div class="flex items-center gap-3 mb-4">
        <div class="w-10 h-10 rounded-xl bg-orange-500/10 flex items-center justify-center">
          <ChartBarIcon class="w-5 h-5 text-orange-500" />
        </div>
        <h2 class="font-bold text-zinc-50">Skills</h2>
      </div>
      <div class="space-y-3 mb-6">
        <div v-for="skill in skills" :key="skill.name">
          <div class="flex justify-between text-sm mb-1">
            <span class="text-zinc-300">{{ skill.name }}</span>
            <span class="text-zinc-500">{{ skill.value }}%</span>
          </div>
          <div class="w-full h-1.5 bg-zinc-800 rounded-full overflow-hidden">
            <div class="h-full bg-orange-500 rounded-full" :style="{ width: skill.value + '%' }"></div>
          </div>
        </div>
      </div>

      <div class="border-t border-zinc-800 pt-6">
        <div class="flex items-center gap-3 mb-4">
          <div class="w-10 h-10 rounded-xl bg-orange-500/10 flex items-center justify-center">
            <GlobeAltIcon class="w-5 h-5 text-orange-500" />
          </div>
          <h2 class="font-bold text-zinc-50">Bahasa</h2>
        </div>
        <div class="space-y-3">
          <div v-for="lang in languages" :key="lang.name" class="flex justify-between items-center text-sm">
            <span class="text-zinc-300">{{ lang.name }}</span>
            <div class="flex gap-1">
              <span
                v-for="n in 5" :key="n"
                class="w-2.5 h-2.5 rounded-full"
                :class="n <= lang.level ? 'bg-orange-500' : 'bg-gray-200'"
              ></span>
            </div>
          </div>
        </div>
      </div>

    </div>

  </div>
</template>
<script setup>
import ProfileCard from './ProfileCard.vue'
import { FolderIcon } from '@heroicons/vue/24/outline'

const repoGroups = [
  {
    account: 'fajarartbekasi',
    url: 'https://github.com/fajarartbekasi',
    stack: 'Laravel',
    color: 'bg-red-600',
    icon: 'La',
    repos: [
      { name: 'KoperasiBMT', desc: 'Sistem informasi koperasi BMT.' },
      { name: 'Perpustakaan', desc: 'Sistem informasi perpustakaan yayasan pendidikan Sumber Daya Insani Bekasi.' },
      { name: 'BabyBekasi', desc: 'Manajemen penjualan.' },
      { name: 'Coffe-ui-dashboard', desc: 'Laravel 5.x front-end preset untuk coffee UI dashboard.' },
      { name: 'smkassalam', desc: 'Monitoring SPP di sekolah.' },
      { name: 'Bumiputera', desc: 'Aplikasi asuransi.' },
      { name: 'akademik', desc: 'Sistem informasi akademik sekolah.' },
      { name: 'sisfo', desc: 'Sistem informasi pesantren.' },
    ],
  },
  {
    account: 'UIDesign-Stack',
    url: 'https://github.com/UIDesign-Stack',
    stack: 'Vue.js',
    color: 'bg-green-600',
    icon: 'Vue',
    repos: [
      { name: 'admira-dashboard', desc: 'Admira Dashboard, dengan Vue, Chart.js, dan Tailwind CSS.' },
      { name: 'Lumina', desc: 'Template web untuk finance dengan Vue.js dan Tailwind CSS.' },
      { name: 'kelaskita', desc: 'Aplikasi sekolah (on going).', icon: 'La', color: 'bg-red-600' },
    ],
  },
]
</script>

<template>
  <ProfileCard />

  <div class="md:col-start-2 md:col-end-4 md:row-start-2 bg-zinc-900/0 rounded-2xl shadow-sm p-8">

    <div class="flex items-center gap-3 mb-6">
      <div class="w-10 h-10 rounded-xl bg-orange-500/10 flex items-center justify-center">
        <FolderIcon class="w-5 h-5 text-orange-500" />
      </div>
      <div>
        <h2 class="font-bold text-zinc-50 text-xl">Portfolio</h2>
        <p class="text-sm text-zinc-400">Kumpulan proyek yang telah saya kerjakan di GitHub.</p>
      </div>
    </div>

    <div class="space-y-8">
      <div v-for="group in repoGroups" :key="group.account">

        <!-- Header akun GitHub -->
        
          <a :href="group.url"
              target="_blank"
              class="flex flex-col sm:flex-row sm:items-center gap-2 sm:gap-3 mb-4 group w-fit max-w-full"
            >
          <div class="w-9 h-9 rounded-full bg-gray-900 flex items-center justify-center flex-shrink-0">
            <svg class="w-5 h-5 text-white" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.207 11.387.6.113.793-.26.793-.577v-2.17c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.729.083-.729 1.205.084 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.42-1.305.763-1.605-2.665-.303-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.3 1.23a11.5 11.5 0 0 1 3.003-.404c1.02.005 2.047.138 3.003.404 2.29-1.552 3.297-1.23 3.297-1.23.653 1.652.24 2.873.118 3.176.77.84 1.233 1.91 1.233 3.22 0 4.61-2.805 5.624-5.478 5.92.43.372.823 1.104.823 2.226v3.3c0 .32.192.694.8.576C20.565 21.795 24 17.297 24 12c0-6.63-5.37-12-12-12z"/>
            </svg>
          </div>
          <div>
            <p class="font-bold text-zinc-50 group-hover:text-orange-500 transition">github.com/{{ group.account }}</p>
            <span
              class="inline-block text-xs font-medium px-2 py-0.5 rounded-full text-white mt-0.5"
              :class="group.color"
            >
              {{ group.stack }}
            </span>
          </div>
        </a>

        <!-- Daftar repo -->
        <div class="grid grid-cols-1 md:grid-cols-2 gap-4">
          <div
            v-for="repo in group.repos"
            :key="repo.name"
            class="border border-zinc-800 rounded-xl p-4 hover:border-orange-200 transition"
          >
            <div class="flex items-center gap-2 mb-1">
              <span
                class="w-6 h-6 rounded-md flex items-center justify-center text-[10px] font-bold text-white flex-shrink-0"
                :class="repo.color || group.color"
                >
                {{ repo.icon || group.icon }}
              </span>
              <h3 class="font-bold text-zinc-50 text-sm">{{ repo.name }}</h3>
            </div>
            <p class="text-xs text-zinc-400 leading-relaxed">{{ repo.desc }}</p>
          </div>
        </div>

      </div>
    </div>

  </div>
</template>
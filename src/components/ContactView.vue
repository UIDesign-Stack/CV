<script setup>
import ProfileCard from './ProfileCard.vue'
import { EnvelopeIcon, PhoneIcon, MapPinIcon } from '@heroicons/vue/24/outline'
import { ref } from 'vue'

const contactInfo = [
  { icon: EnvelopeIcon, label: 'Email', value: 'fajarbekasiediting@email.com' },
  { icon: PhoneIcon, label: 'No. HP / WhatsApp', value: '0812-3456-7890' },
  { icon: MapPinIcon, label: 'Alamat', value: 'Bekasi, Jawa Barat, Indonesia' },
]

const form = ref({ name: '', email: '', message: '' })
const status = ref('') // '', 'sending', 'success', 'error'

async function submitForm() {
  status.value = 'sending'
  try {
    const response = await fetch('https://formspree.io/f/mojgdqgz', {
      method: 'POST',
      headers: { 'Accept': 'application/json' },
      body: JSON.stringify({
        name: form.value.name,
        email: form.value.email,
        message: form.value.message,
      }),
    })

    if (response.ok) {
      status.value = 'success'
      form.value = { name: '', email: '', message: '' }
    } else {
      status.value = 'error'
    }
  } catch (err) {
    status.value = 'error'
  }
}
</script>

<template>
  <ProfileCard />

  <div class="col-start-2 col-end-4 row-start-2 bg-white rounded-2xl shadow-sm p-8">

    <div class="flex items-center gap-3 mb-6">
      <div class="w-10 h-10 rounded-xl bg-orange-100 flex items-center justify-center">
        <EnvelopeIcon class="w-5 h-5 text-orange-500" />
      </div>
      <div>
        <h2 class="font-bold text-gray-900 text-xl">Contact</h2>
        <p class="text-sm text-gray-500">Silakan hubungi saya melalui informasi di bawah ini.</p>
      </div>
    </div>

    <div class="grid grid-cols-2 gap-8">

      <!-- Kiri: Info kontak -->
      <div class="space-y-4">
        <div
          v-for="item in contactInfo"
          :key="item.label"
          class="flex items-center gap-4 border border-gray-100 rounded-2xl p-4"
        >
          <div class="w-11 h-11 rounded-xl bg-orange-50 flex items-center justify-center flex-shrink-0">
            <component :is="item.icon" class="w-5 h-5 text-orange-500" />
          </div>
          <div>
            <p class="text-xs text-gray-500">{{ item.label }}</p>
            <p class="font-medium text-gray-900">{{ item.value }}</p>
          </div>
        </div>

        <!-- Sosial media -->
        <div class="border border-gray-100 rounded-2xl p-4">
          <p class="text-xs text-gray-500 mb-3">Sosial Media</p>
          <div class="flex gap-3">
            <a href="#" class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center hover:bg-gray-200 transition">
              <svg class="w-5 h-5 text-gray-700" fill="currentColor" viewBox="0 0 24 24"><path d="M12 0C5.37 0 0 5.37 0 12c0 5.3 3.438 9.8 8.207 11.387.6.113.793-.26.793-.577v-2.17c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.09-.745.083-.729.083-.729 1.205.084 1.84 1.237 1.84 1.237 1.07 1.834 2.807 1.304 3.492.997.108-.775.42-1.305.763-1.605-2.665-.303-5.466-1.332-5.466-5.93 0-1.31.468-2.38 1.235-3.22-.123-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.3 1.23a11.5 11.5 0 0 1 3.003-.404c1.02.005 2.047.138 3.003.404 2.29-1.552 3.297-1.23 3.297-1.23.653 1.652.24 2.873.118 3.176.77.84 1.233 1.91 1.233 3.22 0 4.61-2.805 5.624-5.478 5.92.43.372.823 1.104.823 2.226v3.3c0 .32.192.694.8.576C20.565 21.795 24 17.297 24 12c0-6.63-5.37-12-12-12z"/></svg>
            </a>
            <a href="#" class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center hover:bg-gray-200 transition">
              <svg class="w-5 h-5 text-gray-700" fill="currentColor" viewBox="0 0 24 24"><path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433a2.062 2.062 0 1 1 0-4.125 2.062 2.062 0 0 1 0 4.125zM7.114 20.452H3.558V9h3.556v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.222 0h.003z"/></svg>
            </a>
            <a href="#" class="w-10 h-10 rounded-full bg-gray-100 flex items-center justify-center hover:bg-gray-200 transition">
              <svg class="w-5 h-5 text-gray-700" fill="none" stroke="currentColor" stroke-width="1.5" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" d="M12 21a9 9 0 1 0 0-18 9 9 0 0 0 0 18Z"/><path stroke-linecap="round" stroke-linejoin="round" d="M3.6 9h16.8M3.6 15h16.8M12 3a15 15 0 0 1 4 9 15 15 0 0 1-4 9 15 15 0 0 1-4-9 15 15 0 0 1 4-9Z"/></svg>
            </a>
          </div>
        </div>
      </div>

      <!-- Kanan: Form kontak -->
      <form @submit.prevent="submitForm" class="border border-gray-100 rounded-2xl p-5 space-y-4">
        <div>
          <label class="text-sm text-gray-600 mb-1 block">Nama</label>
          <input
            v-model="form.name"
            type="text"
            required
            placeholder="Nama Anda"
            class="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:border-orange-400"
          />
        </div>
        <div>
          <label class="text-sm text-gray-600 mb-1 block">Email</label>
          <input
            v-model="form.email"
            type="email"
            required
            placeholder="email@anda.com"
            class="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:border-orange-400"
          />
        </div>
        <div>
          <label class="text-sm text-gray-600 mb-1 block">Pesan</label>
          <textarea
            v-model="form.message"
            rows="4"
            required
            placeholder="Tulis pesan Anda..."
            class="w-full border border-gray-200 rounded-xl px-4 py-2.5 text-sm focus:outline-none focus:border-orange-400 resize-none"
          ></textarea>
        </div>
        <button
          type="submit"
          :disabled="status === 'sending'"
          class="w-full bg-orange-500 hover:bg-orange-600 disabled:opacity-50 text-white py-2.5 rounded-xl font-medium transition"
        >
          {{ status === 'sending' ? 'Mengirim...' : 'Kirim Pesan' }}
        </button>

        <p v-if="status === 'success'" class="text-green-600 text-sm text-center">
          Pesan berhasil terkirim! Terima kasih sudah menghubungi.
        </p>
        <p v-if="status === 'error'" class="text-red-500 text-sm text-center">
          Gagal mengirim pesan. Coba lagi nanti.
        </p>
      </form>

    </div>

  </div>
</template>
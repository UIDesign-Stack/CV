<script setup>
import { ref, provide } from 'vue'
import Sidebar from './components/Sidebar.vue'
import ProfileCard from './components/ProfileCard.vue'
import ExperienceSkills from './components/ExperienceSkills.vue'
import EducationView from './components/EducationView.vue'
import ExperienceView from './components/ExperienceView.vue'
import SkillsView from './components/SkillsView.vue'
import PortfolioView from './components/PortfolioView.vue'
import CertificatesView from './components/CertificatesView.vue'
import ContactView from './components/ContactView.vue'

const activeMenu = ref('About Me')

function setActiveMenu(name) {
  activeMenu.value = name
}

provide('setActiveMenu', setActiveMenu)

const viewMap = {
  'Education': EducationView,
  'Experience': ExperienceView,
  'Skills': SkillsView,
  'Portfolio': PortfolioView,
  'Certificates': CertificatesView,
  'Contact': ContactView,
}
</script>

<template>
  <main class="min-h-screen bg-gray-100 p-8">
    <div class="grid grid-cols-[320px_1fr_380px] grid-rows-[auto_auto] gap-6">
      <Sidebar :active-menu="activeMenu" @update:active-menu="activeMenu = $event" />

      <template v-if="activeMenu === 'About Me'">
        <ProfileCard />
        <ExperienceSkills />
      </template>

      <component v-else :is="viewMap[activeMenu]" />
    </div>
  </main>
</template>
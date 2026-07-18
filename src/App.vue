<script setup>
import { ref, provide, onMounted, onUnmounted } from 'vue'
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
function setActiveMenu(name) { activeMenu.value = name }
provide('setActiveMenu', setActiveMenu)

const viewMap = {
  'Education': EducationView,
  'Experience': ExperienceView,
  'Skills': SkillsView,
  'Portfolio': PortfolioView,
  'Certificates': CertificatesView,
  'Contact': ContactView,
}

// ---------- Particle background (global) ----------
const canvasRef = ref(null)
let ctx, canvas, animationId
let particles = [], fireworkParticles = [], dustParticles = []
let frameCount = 0
let autoDrift = true
const mouse = { x: null, y: null }

class Particle {
  constructor(x, y, isFirework = false) {
    const baseSpeed = isFirework ? Math.random() * 2 + 1 : Math.random() * 0.5 + 0.3
    Object.assign(this, {
      isFirework, x, y,
      vx: Math.cos(Math.random() * Math.PI * 3) * baseSpeed,
      vy: Math.sin(Math.random() * Math.PI * 3) * baseSpeed,
      size: isFirework ? Math.random() * 4 + 3 : Math.random() * 5 + 3,
      hue: Math.random() * 360,
      alpha: 1,
      sizeDirection: Math.random() < 0.5 ? -1 : 1,
      trail: [],
    })
  }
  update() {
    const dist = mouse.x !== null ? (mouse.x - this.x) ** 2 + (mouse.y - this.y) ** 2 : 0
    if (!this.isFirework) {
      const force = dist && dist < 12000 ? (12000 - dist) / 12000 : 0
      if (mouse.x === null && autoDrift) {
        this.vx += (Math.random() - 0.5) * 0.03
        this.vy += (Math.random() - 0.5) * 0.03
      }
      if (dist) {
        const sqrtDist = Math.sqrt(dist)
        this.vx += ((mouse.x - this.x) / sqrtDist) * force * 0.1
        this.vy += ((mouse.y - this.y) / sqrtDist) * force * 0.1
      }
      this.vx *= mouse.x !== null ? 0.99 : 0.998
      this.vy *= mouse.y !== null ? 0.99 : 0.998
    } else {
      this.alpha -= 0.02
    }
    this.x += this.vx
    this.y += this.vy
    if (this.x <= 0 || this.x >= canvas.width - 1) this.vx *= -0.9
    if (this.y < 0 || this.y > canvas.height) this.vy *= -0.9
    this.size += this.sizeDirection * 0.08
    if (this.size > 4.5 || this.size < 1.5) this.sizeDirection *= -1
    this.hue = (this.hue + 0.3) % 360
    if (frameCount % 2 === 0 && (Math.abs(this.vx) > 0.1 || Math.abs(this.vy) > 0.1)) {
      this.trail.push({ x: this.x, y: this.y, hue: this.hue, alpha: this.alpha })
      if (this.trail.length > 10) this.trail.shift()
    }
  }
  draw() {
    const gradient = ctx.createRadialGradient(this.x, this.y, 0, this.x, this.y, this.size)
    gradient.addColorStop(0, `hsla(${this.hue}, 90%, 60%, ${Math.max(this.alpha, 0)})`)
    gradient.addColorStop(1, `hsla(${this.hue + 30}, 90%, 50%, 0)`)
    ctx.fillStyle = gradient
    ctx.beginPath()
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2)
    ctx.fill()
    if (this.trail.length > 1) {
      ctx.beginPath()
      ctx.lineWidth = 1
      for (let i = 0; i < this.trail.length - 1; i++) {
        const { x: x1, y: y1, hue: h1, alpha: a1 } = this.trail[i]
        const { x: x2, y: y2 } = this.trail[i + 1]
        ctx.strokeStyle = `hsla(${h1}, 90%, 60%, ${Math.max(a1 * 0.4, 0)})`
        ctx.moveTo(x1, y1)
        ctx.lineTo(x2, y2)
      }
      ctx.stroke()
    }
  }
  isDead() { return this.isFirework && this.alpha <= 0 }
}

class DustParticle {
  constructor() {
    Object.assign(this, {
      x: Math.random() * canvas.width, y: Math.random() * canvas.height,
      size: Math.random() * 1.2 + 0.4,
      vx: (Math.random() - 0.5) * 0.05, vy: (Math.random() - 0.5) * 0.05,
    })
  }
  update() {
    this.x = (this.x + this.vx + canvas.width) % canvas.width
    this.y = (this.y + this.vy + canvas.height) % canvas.height
  }
  draw() {
    ctx.fillStyle = `rgba(200, 200, 200, 0.2)`
    ctx.beginPath()
    ctx.arc(this.x, this.y, this.size, 0, Math.PI * 2)
    ctx.fill()
  }
}

function adjustParticleCount() {
  const area = canvas.width * canvas.height
  return Math.max(40, Math.min(90, Math.floor(area / 12000)))
}

function createParticles() {
  particles = []
  dustParticles = []
  const n = adjustParticleCount()
  for (let i = 0; i < n; i++) {
    particles.push(new Particle(Math.random() * canvas.width, Math.random() * canvas.height))
  }
  for (let i = 0; i < 80; i++) {
    dustParticles.push(new DustParticle())
  }
}

function connectParticles() {
  ctx.lineWidth = 1
  for (let i = 0; i < particles.length; i++) {
    for (let j = i + 1; j < particles.length; j++) {
      const p = particles[i], q = particles[j]
      const dist = (p.x - q.x) ** 2 + (p.y - q.y) ** 2
      if (dist < 9000) {
        const mixHue = (p.hue + q.hue) / 2
        ctx.strokeStyle = `hsla(${mixHue}, 90%, 60%, ${0.35 * (1 - Math.sqrt(dist) / 95)})`
        ctx.beginPath()
        ctx.moveTo(p.x, p.y)
        ctx.lineTo(q.x, q.y)
        ctx.stroke()
      }
    }
  }
}

function animate() {
  ctx.clearRect(0, 0, canvas.width, canvas.height)
  ;[dustParticles, particles, fireworkParticles].forEach(arr => {
    for (let i = arr.length - 1; i >= 0; i--) {
      arr[i].update()
      arr[i].draw()
      if (arr[i].isDead?.()) arr.splice(i, 1)
    }
  })
  connectParticles()
  frameCount++
  animationId = requestAnimationFrame(animate)
}

function resizeCanvas() {
  canvas.width = window.innerWidth
  canvas.height = window.innerHeight
  createParticles()
}

function handleMouseMove(e) {
  mouse.x = e.clientX
  mouse.y = e.clientY
  autoDrift = false
}
function handleMouseLeave() {
  mouse.x = null
  mouse.y = null
  autoDrift = true
}
function handleClick(e) {
  for (let i = 0; i < 12; i++) {
    const angle = Math.random() * Math.PI * 2
    const speed = Math.random() * 4 + 1.5
    const p = new Particle(e.clientX, e.clientY, true)
    p.vx = Math.cos(angle) * speed
    p.vy = Math.sin(angle) * speed
    fireworkParticles.push(p)
  }
}

onMounted(() => {
  canvas = canvasRef.value
  ctx = canvas.getContext('2d')
  resizeCanvas()
  animate()
  window.addEventListener('mousemove', handleMouseMove)
  window.addEventListener('mouseleave', handleMouseLeave)
  window.addEventListener('click', handleClick)
  window.addEventListener('resize', resizeCanvas)
})
onUnmounted(() => {
  cancelAnimationFrame(animationId)
  window.removeEventListener('mousemove', handleMouseMove)
  window.removeEventListener('mouseleave', handleMouseLeave)
  window.removeEventListener('click', handleClick)
  window.removeEventListener('resize', resizeCanvas)
})
</script>

<template>
  <main class="min-h-screen bg-zinc-950 p-8 relative overflow-hidden">

    <canvas ref="canvasRef" class="fixed inset-0 w-full h-full pointer-events-none"></canvas>

    <div class="relative z-10 grid grid-cols-1 md:grid-cols-[320px_1fr_380px] md:grid-rows-[auto_auto] gap-6">
      <Sidebar :active-menu="activeMenu" @update:active-menu="activeMenu = $event" />

      <template v-if="activeMenu === 'About Me'">
        <ProfileCard />
        <ExperienceSkills />
      </template>

      <component v-else :is="viewMap[activeMenu]" />
    </div>
  </main>
</template>
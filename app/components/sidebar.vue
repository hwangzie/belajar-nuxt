<template>
  <div class="sidebar-shell">
    <button class="menu-toggle" type="button" aria-label="Toggle sidebar" @click="isOpen = !isOpen">
      ☰
    </button>

    <aside :class="['sidebar', { 'sidebar-open': isOpen }]" aria-label="Sidebar navigation">
      <div class="sidebar-header">
        <div class="brand">Dashboard</div>
        <button class="close-btn" type="button" aria-label="Close sidebar" @click="isOpen = false">
          ×
        </button>
      </div>

      <nav class="nav">
        <NuxtLink class="nav-item active" to="/">
          <span>🏠</span>
          <span>Home</span>
        </NuxtLink>
        <NuxtLink class="nav-item" to="/about">
          <span>📄</span>
          <span>About</span>
        </NuxtLink>
        <NuxtLink class="nav-item" to="/contact">
          <span>📞</span>
          <span>Contact</span>
        </NuxtLink>
        <NuxtLink class="nav-item" to="/settings">
          <span>⚙️</span>
          <span>Settings</span>
        </NuxtLink>
      </nav>
    </aside>

    <div :class="['backdrop', { visible: isOpen }]" @click="isOpen = false" />

    <main class="content">
      <slot />
    </main>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue'

const isOpen = ref(false)
</script>

<style scoped>
:global(body) {
  margin: 0;
  font-family: Arial, sans-serif;
  background: #f3f4f6;
}

.sidebar-shell {
  position: relative;
  display: flex;
  min-height: 100vh;
}

.sidebar {
  position: fixed;
  top: 0;
  left: 0;
  z-index: 40;
  display: flex;
  flex-direction: column;
  width: 260px;
  height: 100vh;
  background: linear-gradient(180deg, #111827 0%, #1f2937 100%);
  color: #f9fafb;
  box-shadow: 0 10px 30px rgba(15, 23, 42, 0.25);
  transform: translateX(-100%);
  transition: transform 0.25s ease;
}

.sidebar-open {
  transform: translateX(0);
}

.sidebar-header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1.25rem 1rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.08);
}

.brand {
  font-size: 1.1rem;
  font-weight: 700;
  letter-spacing: 0.04em;
}

.close-btn,
.menu-toggle {
  border: 0;
  background: transparent;
  color: inherit;
  cursor: pointer;
}

.close-btn {
  font-size: 1.5rem;
  line-height: 1;
}

.nav {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
  padding: 1rem 0.75rem;
}

.nav-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.8rem 0.9rem;
  border-radius: 0.75rem;
  color: #d1d5db;
  text-decoration: none;
  transition: background 0.2s ease, color 0.2s ease;
}

.nav-item:hover,
.nav-item.active {
  background: rgba(255, 255, 255, 0.08);
  color: #ffffff;
}

.content {
  flex: 1;
  min-width: 0;
  padding: 1.5rem;
}

.backdrop {
  position: fixed;
  inset: 0;
  z-index: 30;
  background: rgba(15, 23, 42, 0.45);
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.25s ease;
}

.backdrop.visible {
  opacity: 1;
  pointer-events: auto;
}

.menu-toggle {
  position: fixed;
  top: 1rem;
  left: 1rem;
  z-index: 50;
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 2.8rem;
  height: 2.8rem;
  border-radius: 0.75rem;
  background: #111827;
  color: white;
  font-size: 1.3rem;
  box-shadow: 0 8px 16px rgba(15, 23, 42, 0.2);
}

@media (min-width: 768px) {
  .sidebar {
    position: sticky;
    transform: none;
    box-shadow: none;
  }

  .menu-toggle,
  .close-btn,
  .backdrop {
    display: none;
  }

  .sidebar-shell {
    min-height: 100vh;
  }

  .content {
    padding: 2rem;
  }
}
</style>

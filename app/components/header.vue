<script setup>
const isMenuOpen = ref(false)

const navLinks = [
  { label: 'Home', to: '/' },
  { label: 'About', to: '/about' },
  { label: 'Courses', to: '/courses' },
  { label: 'Contact', to: '/contact' },
]

const closeMenu = () => {
  isMenuOpen.value = false
}
</script>

<template>
  <header class="site-header">
    <div class="container header-inner">
      <NuxtLink to="/" class="brand" aria-label="Home" @click="closeMenu">Belajar Nuxt</NuxtLink>

      <button
        class="nav-toggle"
        type="button"
        aria-label="Toggle navigation"
        :aria-expanded="isMenuOpen"
        @click="isMenuOpen = !isMenuOpen"
      >
        <span></span>
        <span></span>
        <span></span>
      </button>

      <nav class="main-nav" :class="{ 'is-open': isMenuOpen }" aria-label="Main navigation">
        <NuxtLink v-for="link in navLinks" :key="link.to" :to="link.to" class="nav-link" @click="closeMenu">
          {{ link.label }}
        </NuxtLink>
      </nav>

      <NuxtLink to="/login" class="cta-button" @click="closeMenu">Login</NuxtLink>
    </div>
  </header>
</template>

<style scoped>
  .site-header {
    position: sticky;
    top: 0;
    z-index: 10;
    background: rgba(15, 23, 42, 0.9);
    backdrop-filter: blur(10px);
    border-bottom: 1px solid rgba(148, 163, 184, 0.2);
  }

  .container {
    width: min(1120px, calc(100% - 2rem));
    margin: 0 auto;
  }

  .header-inner {
    display: flex;
    align-items: center;
    justify-content: space-between;
    min-height: 72px;
    gap: 1rem;
    position: relative;
  }

  .brand {
    font-size: 1.25rem;
    font-weight: 700;
    color: #f8fafc;
    text-decoration: none;
    letter-spacing: 0.02em;
    white-space: nowrap;
  }

  .main-nav {
    display: flex;
    align-items: center;
    justify-content: center;
    gap: 1.5rem;
    flex-wrap: wrap;
    flex: 1;
  }

  .nav-link {
    color: #cbd5e1;
    text-decoration: none;
    font-weight: 500;
    transition: color 0.2s ease;
  }

  .nav-link:hover,
  .nav-link:focus-visible,
  .nav-link.router-link-active {
    color: #fff;
  }

  .cta-button {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    padding: 0.7rem 1.2rem;
    border-radius: 999px;
    background: #38bdf8;
    color: #082f49;
    text-decoration: none;
    font-weight: 700;
    transition: transform 0.2s ease, opacity 0.2s ease;
    white-space: nowrap;
  }

  .cta-button:hover,
  .cta-button:focus-visible {
    transform: translateY(-1px);
    opacity: 0.95;
  }

  .nav-toggle {
    display: none;
    background: transparent;
    border: 0;
    padding: 0.25rem;
    cursor: pointer;
    margin-left: auto;
  }

  .nav-toggle span {
    display: block;
    width: 22px;
    height: 2px;
    background: #f8fafc;
    border-radius: 999px;
    margin: 5px 0;
  }

  @media (max-width: 768px) {
    .header-inner {
      flex-wrap: wrap;
      padding: 0.75rem 0;
    }

    .main-nav {
      order: 3;
      width: 100%;
      display: none;
      padding-top: 0.5rem;
      gap: 0.75rem 1rem;
    }

    .main-nav.is-open {
      display: flex;
    }

    .nav-toggle {
      display: block;
    }
  }

  @media (max-width: 640px) {
    .header-inner {
      gap: 0.5rem;
    }

    .brand {
      font-size: 1.1rem;
    }

    .cta-button {
      padding: 0.6rem 1rem;
      font-size: 0.95rem;
    }
  }
</style>

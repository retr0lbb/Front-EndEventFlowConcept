<template>
  <header>
    <div class="nav-inner">
      <RouterLink to="/" class="logo">EventFlow<span class="logo-dot">.</span></RouterLink>
      <nav>
        <a href="#" class="active">Discover</a>
        <a href="#">Schedule</a>
        <a href="#">Speakers</a>
        <a href="#">Venues</a>
      </nav>
      <div class="nav-actions">
        <button class="theme-toggle" :class="{ light: !isDark }" @click="toggle" :title="isDark ? 'Switch to light mode' : 'Switch to dark mode'">
          <span class="theme-emoji">{{ isDark ? '🌙' : '☀️' }}</span>
        </button>
        <RouterLink to="/login" class="btn-signin">Sign In</RouterLink>
        <button class="btn-primary">Create Event</button>
        <button class="icon-btn">
          <span class="material-symbols-outlined">notifications</span>
        </button>
        <button class="icon-btn">
          <span class="material-symbols-outlined">account_circle</span>
        </button>
      </div>
    </div>
  </header>
</template>

<script setup lang="ts">
import { RouterLink } from 'vue-router'
import { useTheme } from '@/composables/useTheme'

const { isDark, toggle } = useTheme()
</script>

<style scoped>
header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: var(--bg-nav);
  backdrop-filter: blur(20px);
  border-bottom: 1px solid var(--border);
  transition: var(--transition-theme);
}

.nav-inner {
  max-width: 1440px;
  margin: 0 auto;
  padding: 0 2rem;
  height: 68px;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.logo {
  font-family: 'Syne', sans-serif;
  font-size: 1.4rem;
  font-weight: 800;
  color: var(--text);
  letter-spacing: -0.04em;
  display: flex;
  align-items: center;
  gap: 0.4rem;
}

.logo-dot {
  color: var(--emerald);
  font-size: 1.8rem;
  line-height: 1;
}

nav {
  display: flex;
  gap: 2rem;
  align-items: center;
}

nav a {
  color: var(--text-muted);
  text-decoration: none;
  font-size: 0.9rem;
  font-weight: 500;
  letter-spacing: 0.01em;
  transition: color 0.2s;
}

nav a.active,
nav a:hover {
  color: var(--emerald);
}

nav a.active {
  position: relative;
}

nav a.active::after {
  content: '';
  position: absolute;
  bottom: -22px;
  left: 0;
  right: 0;
  height: 2px;
  background: var(--emerald);
  border-radius: 2px;
}

.nav-actions {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.theme-toggle {
  width: 38px;
  height: 38px;
  border-radius: 50%;
  border: 1px solid var(--border-strong);
  background: var(--bg-elevated);
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: border-color 0.2s, background 0.2s, transform 0.2s;
  overflow: hidden;
}

.theme-toggle:hover {
  border-color: var(--emerald-border);
  background: var(--emerald-glow);
  transform: scale(1.08);
}

.theme-emoji {
  font-size: 1.1rem;
  line-height: 1;
  display: block;
  animation: theme-spin 0.45s cubic-bezier(0.34, 1.56, 0.64, 1);
}

@keyframes theme-spin {
  0%   { transform: rotate(-90deg) scale(0.5); opacity: 0; }
  100% { transform: rotate(0deg)   scale(1);   opacity: 1; }
}

.btn-signin {
  background: transparent;
  color: var(--text-muted);
  border: 1px solid var(--border-strong);
  padding: 0.5rem 1.2rem;
  border-radius: 8px;
  font-family: 'DM Sans', sans-serif;
  font-weight: 600;
  font-size: 0.875rem;
  text-decoration: none;
  transition: all 0.2s;
}

.btn-signin:hover {
  color: var(--emerald);
  border-color: var(--emerald-border);
  background: var(--emerald-glow);
}
</style>

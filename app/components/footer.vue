<template>
  <footer class="site-footer">
    <div class="footer-inner">
      <div class="footer-brand">
        <h3>Belajar Nuxt</h3>
        <p>
          Belajar modern dengan project Nuxt yang cepat, responsif, dan mudah dikembangkan.
        </p>
      </div>

      <nav class="footer-links" aria-label="Footer navigation">
        <h4>Menu</h4>
        <ul>
          <li><a href="#">Home</a></li>
          <li><a href="#">Features</a></li>
          <li><a href="#">Pricing</a></li>
          <li><a href="#">Contact</a></li>
        </ul>
      </nav>

      <div class="footer-social">
        <h4>Follow Us</h4>
        <div class="social-list">
          <a href="#" aria-label="Instagram">Instagram</a>
          <a href="#" aria-label="Twitter">Twitter</a>
          <a href="#" aria-label="GitHub">GitHub</a>
        </div>
      </div>
    </div>

    <div class="footer-bottom">
      <p>© 2026 Belajar Nuxt. All rights reserved.</p>
    </div>
  </footer>
</template>

<style scoped>
.site-footer {
  background: #0f172a;
  color: #e2e8f0;
  width: 100%;
}

.footer-inner {
  max-width: 1200px;
  margin: 0 auto;
  padding: 3rem 1.25rem 2rem;
  display: grid;
  grid-template-columns: 1.5fr 1fr 1fr;
  gap: 2rem;
  align-items: start;
}

.footer-brand h3,
.footer-links h4,
.footer-social h4 {
  margin: 0 0 1rem;
  color: #ffffff;
  font-size: 1.05rem;
  font-weight: 700;
}

.footer-brand p {
  margin: 0;
  color: #cbd5e1;
  line-height: 1.7;
  max-width: 28rem;
}

.footer-links ul,
.social-list {
  list-style: none;
  margin: 0;
  padding: 0;
  display: flex;
  flex-direction: column;
  gap: 0.65rem;
}

.footer-links a,
.social-list a {
  color: #cbd5e1;
  text-decoration: none;
  transition: color 0.2s ease;
}

.footer-links a:hover,
.social-list a:hover {
  color: #ffffff;
}

.footer-bottom {
  border-top: 1px solid rgba(148, 163, 184, 0.25);
  text-align: center;
  padding: 1rem 1.25rem;
  color: #cbd5e1;
  font-size: 0.92rem;
}

.footer-bottom p {
  margin: 0;
}

@media (max-width: 768px) {
  .footer-inner {
    grid-template-columns: 1fr;
    gap: 1.5rem;
    padding: 2.5rem 1rem 1.5rem;
    text-align: center;
  }

  .footer-brand p {
    max-width: 100%;
  }

  .footer-links ul,
  .social-list {
    align-items: center;
  }
}
</style>

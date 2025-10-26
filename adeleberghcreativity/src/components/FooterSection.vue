<script setup lang="ts">
const currentYear = new Date().getFullYear()
</script>

<template>
  <footer class="footer-section">
    <div class="footer-container">
      <div class="footer-content">
        <div class="footer-brand">
          <img src="/icon.svg" alt="Adele Bergh Creativity" class="footer-logo" />
          <h3>Adele Bergh Creativity</h3>
        </div>

        <div class="footer-links">
          <div class="footer-column">
            <h4>Connect</h4>
            <ul>
              <li><a href="#" target="_blank" rel="noopener">Instagram</a></li>
              <li><a href="#" target="_blank" rel="noopener">Facebook</a></li>
              <li><a href="#" target="_blank" rel="noopener">Email</a></li>
            </ul>
          </div>

          <div class="footer-column">
            <h4>Explore</h4>
            <ul>
              <li><a href="#about">About</a></li>
              <li><a href="#paintings">Paintings</a></li>
              <li><a href="#photos">Photography</a></li>
            </ul>
          </div>
        </div>
      </div>

      <div class="footer-bottom">
        <p>&copy; {{ currentYear }} Adele Bergh Creativity. All rights reserved.</p>
      </div>
    </div>
  </footer>
</template>

<style scoped>
.footer-section {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 3rem 2rem 1.5rem;
}

.footer-container {
  max-width: 1200px;
  margin: 0 auto;
}

.footer-content {
  display: grid;
  grid-template-columns: 1fr 2fr;
  gap: 3rem;
  padding-bottom: 2rem;
  border-bottom: 1px solid rgba(255, 255, 255, 0.2);
}

.footer-brand {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}

.footer-logo {
  width: 60px;
  height: 60px;
  filter: brightness(0) invert(1);
}

.footer-brand h3 {
  font-size: 1.5rem;
  font-weight: 600;
  margin: 0;
}

.footer-links {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 2rem;
}

.footer-column h4 {
  font-size: 1.1rem;
  font-weight: 600;
  margin-bottom: 1rem;
  color: rgba(255, 255, 255, 0.95);
}

.footer-column ul {
  list-style: none;
  padding: 0;
  margin: 0;
  display: flex;
  flex-direction: column;
  gap: 0.75rem;
}

.footer-column a {
  color: rgba(255, 255, 255, 0.8);
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-column a:hover {
  color: white;
}

.footer-bottom {
  padding-top: 2rem;
  text-align: center;
}

.footer-bottom p {
  color: rgba(255, 255, 255, 0.8);
  font-size: 0.95rem;
  margin: 0;
}

@media (max-width: 768px) {
  .footer-section {
    padding: 2rem 1rem 1rem;
  }

  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
  }

  .footer-links {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .footer-brand h3 {
    font-size: 1.25rem;
  }

  .footer-logo {
    width: 50px;
    height: 50px;
  }
}
</style>

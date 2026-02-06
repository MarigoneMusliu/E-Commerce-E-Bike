<template>
  <div class="footer-wrap text-light">
    <div class="container py-5">
      <div class="row g-4 footer-grid">
        <div class="col-lg-3 col-md-6">
          <div class="brand">
            <div class="brand-logo">
              <i class="bi bi-bicycle"></i>
            </div>
            <h5 class="mb-2">E‑Bike Marketplace</h5>
            <p class="muted">
              Premium electric bikes, accessories, and service — built for the
              city and the trail.
            </p>
            <div class="mini-badges">
              <span><i class="bi bi-shield-check"></i> Warranty</span>
              <span><i class="bi bi-lightning-charge"></i> Fast Charging</span>
              <span><i class="bi bi-truck"></i> Fast Delivery</span>
            </div>
          </div>
        </div>

        <div class="col-lg-2 col-md-6">
          <h6 class="text-uppercase fw-bold mb-3">Quick Links</h6>
          <ul class="footer-links">
            <li><a href="/">Home</a></li>
            <li><a href="/favorites">Favorites</a></li>
            <li><a href="/cart">Cart</a></li>
            <li><a href="/account">Account</a></li>
          </ul>
        </div>

        <div class="col-lg-3 col-md-6">
          <h6 class="text-uppercase fw-bold mb-3">Join the Ride</h6>
          <div class="newsletter">
            <input type="email" placeholder="Email address" />
            <button class="btn btn-danger">Subscribe</button>
          </div>
          <small class="muted d-block mt-2"
            >No spam, unsubscribe anytime.</small
          >
          <div class="social-icons mt-3">
            <a
              href="https://www.instagram.com/marigonamusliuu_/"
              target="_blank"
              class="social-icon"
            >
              <i class="bi bi-instagram"></i>
            </a>
            <a
              href="https://www.facebook.com/"
              target="_blank"
              class="social-icon"
            >
              <i class="bi bi-facebook"></i>
            </a>
            <a
              href="https://twitter.com/?lang=en"
              target="_blank"
              class="social-icon"
            >
              <i class="bi bi-twitter"></i>
            </a>
            <a
              href="https://www.linkedin.com/in/marigon%C3%AB-musliu-a4a3b1245/"
              target="_blank"
              class="social-icon"
            >
              <i class="bi bi-linkedin"></i>
            </a>
          </div>
        </div>

        <div class="col-lg-4 col-md-6">
          <h6 class="text-uppercase fw-bold mb-3">Contact</h6>
          <div class="contact-details">
            <p><i class="bi bi-geo-alt me-2"></i> Isa Boletini, Gjilan</p>
            <p>
              <i class="bi bi-envelope me-2"></i> marigonamusliu48@gmail.com
            </p>
            <p><i class="bi bi-telephone me-2"></i> + 383 49 733 741</p>
          </div>
          <div class="map-frame mt-3">
            <iframe
              width="100%"
              height="220"
              src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d4443.367635626963!2d21.212789658287206!3d42.464722012073625!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1354598a2583b925%3A0xb2d2fc1935c8e560!2sIsa%20Boletini%2C%20Gjilan!5e0!3m2!1sen!2s!4v1678998798245!5m2!1sen!2s"
              allowfullscreen=""
              loading="lazy"
            >
            </iframe>
          </div>
        </div>
      </div>

      <div class="footer-divider"></div>

      <div
        class="bottom-row d-flex flex-wrap justify-content-between align-items-center gap-3"
      >
        <p class="mb-0 muted">&copy; 2025 E‑Commerce | All Rights Reserved</p>
        <div class="payments">
          <span><i class="bi bi-credit-card"></i> Visa</span>
          <span><i class="bi bi-credit-card-2-front"></i> MasterCard</span>
          <span><i class="bi bi-shield-lock"></i> Secure Checkout</span>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.footer-wrap {
  background:
    radial-gradient(circle at top, rgba(57, 178, 191, 0.2), transparent 55%),
    linear-gradient(180deg, #0b1016 0%, #0a0f14 100%);
  border-top: 1px solid rgba(255, 255, 255, 0.08);
}

.muted {
  color: #b8c6d4;
}

.footer-grid h6 {
  letter-spacing: 0.08em;
}

.brand {
  background: rgba(255, 255, 255, 0.03);
  border: 1px solid rgba(255, 255, 255, 0.06);
  border-radius: 16px;
  padding: 18px;
}

.brand-logo {
  width: 46px;
  height: 46px;
  border-radius: 12px;
  display: grid;
  place-items: center;
  background: linear-gradient(135deg, #0b7e7c, #39b2bf, #75cff5);
  margin-bottom: 12px;
}

.brand-logo i {
  font-size: 22px;
}

.mini-badges {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
  margin-top: 10px;
}

.mini-badges span {
  font-size: 12px;
  padding: 4px 8px;
  border-radius: 999px;
  background: rgba(57, 178, 191, 0.18);
  color: #dff6fb;
  border: 1px solid rgba(117, 207, 245, 0.25);
}

.footer-links {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer-links li + li {
  margin-top: 8px;
}

.footer-links a {
  color: #d5e6f2;
  text-decoration: none;
}

.footer-links a:hover {
  color: #75cff5;
}

.newsletter {
  display: flex;
  gap: 8px;
}

.newsletter input {
  flex: 1;
  border-radius: 10px;
  border: 1px solid rgba(255, 255, 255, 0.08);
  background: rgba(255, 255, 255, 0.04);
  color: #ffffff;
  padding: 10px 12px;
}

.newsletter input::placeholder {
  color: #b7c7d6;
}

.social-icons {
  display: flex;
  gap: 12px;
}

.social-icon i {
  font-size: 22px;
  color: #e6f3fb;
  transition:
    transform 0.2s ease,
    color 0.2s ease;
}

.social-icon i:hover {
  transform: translateY(-2px);
  color: #75cff5;
}

.contact-details p {
  margin-bottom: 10px;
}

.map-frame {
  position: relative;
  overflow: hidden;
  border-radius: 14px;
  background: rgba(0, 0, 0, 0.12);
  box-shadow: 0 8px 20px rgba(2, 6, 23, 0.35);
}

.map-frame iframe {
  transition: transform 0.3s ease;
}

.map-frame iframe:hover {
  transform: scale(1.03);
}

.footer-divider {
  height: 1px;
  margin: 26px 0 18px;
  background: rgba(255, 255, 255, 0.08);
}

.bottom-row .payments {
  display: flex;
  gap: 14px;
  flex-wrap: wrap;
  color: #c7d7e6;
}

.bottom-row .payments i {
  margin-right: 6px;
  color: #75cff5;
}

@media (max-width: 768px) {
  .newsletter {
    flex-direction: column;
  }
}
</style>

<template>
  <div class="container-fluid bg-dark text-light">
    <footer class="footer-container d-flex flex-wrap justify-content-between align-items-start text-sm-start py-5">
      
      <!-- Copyright Section -->
      <div class="col-md-3 copyright text-center text-md-start">
        <p class="mb-0">
          &copy; 2025 E-Commerce | All Rights Reserved
        </p>
      </div>

      <!-- Social Media Section -->
      <div class="col-md-3 d-flex flex-column align-items-center s-media">
        <h6 class="text-uppercase fw-bold mb-4 text-center">Follow Us</h6>
        <div class="d-flex gap-4 justify-content-center social-icons">
          <a href="https://www.instagram.com/marigonamusliuu_/" target="_blank" class="social-icon">
            <i class="bi bi-instagram"></i>
          </a>
          <a href="https://www.facebook.com/" target="_blank" class="social-icon">
            <i class="bi bi-facebook"></i>
          </a>
          <a href="https://twitter.com/?lang=en" target="_blank" class="social-icon">
            <i class="bi bi-twitter"></i>
          </a>
          <a href="https://www.linkedin.com/in/marigon%C3%AB-musliu-a4a3b1245/" target="_blank" class="social-icon">
            <i class="bi bi-linkedin"></i>
          </a>
        </div>
      </div>

      <!-- Contact Section -->
      <div class="col-md-3 contact">
        <h6 class="text-uppercase fw-bold mb-4 text-center">Contact</h6>
        <div class="contact-details">
          <p><i class="bi bi-geo-alt me-2"></i> Isa Boletini, Gjilan</p>
          <p><i class="bi bi-envelope me-2"></i> marigonamusliu48@gmail.com</p>
          <p><i class="bi bi-telephone me-2"></i> + 383 49 733 741</p>
        </div>
      </div>

      <!-- Google Map Section with Parallax -->
      <div class="col-md-3 map-container">
        <h6 class="text-uppercase fw-bold mb-4 text-center">Find Us</h6>
        <div class="map-frame">
          <iframe
            width="100%"
            height="300"
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d4443.367635626963!2d21.212789658287206!3d42.464722012073625!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x1354598a2583b925%3A0xb2d2fc1935c8e560!2sIsa%20Boletini%2C%20Gjilan!5e0!3m2!1sen!2s!4v1678998798245!5m2!1sen!2s"
            allowfullscreen=""
            loading="lazy">
          </iframe>
        </div>
      </div>

    </footer>
  </div>
</template>

<style scoped>
/* Global Styles */
footer {
  background-color: #343a40;
  color: #fff;
  padding: 50px 0;
  border-top: 2px solid #fff;
  transition: all 0.3s ease;
}

footer a {
  color: inherit;
  text-decoration: none;
  transition: transform 0.3s ease, color 0.3s ease;
}

footer a:hover {
  color: #fff;
  transform: scale(1.1);
}

footer i {
  font-size: 2rem;
  transition: color 0.3s ease, transform 0.3s ease;
}

footer i:hover {
  color: #fff;
  transform: scale(1.2);
}

/* Social Media Icons */
.social-icons {
  display: flex;
  gap: 20px;
  justify-content: center;
}

.social-icon i {
  font-size: 2.5rem;
  color: #fff;
}

.social-icon:hover i {
  color: #fff;
  transform: scale(1.2);
}

/* Contact Section */
.contact-details p {
  font-size: 1.1rem;
  margin-bottom: 15px;
}

.contact-details i {
  font-size: 1.2rem;
}

/* Parallax Map */
.map-frame {
  position: relative;
  overflow: hidden;
  border-radius: 10px;
  background: rgba(0, 0, 0, 0.1);
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.3);
}

/* Footer layout and responsiveness */
.footer-container {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
}

.footer-container .col-md-3 {
  flex: 1;
}

/* Responsive layout */
@media (max-width: 768px) {
  footer {
    flex-direction: column;
    align-items: center;
    text-align: center;
  }

  .social-icons {
    flex-direction: column;
    gap: 15px;
  }

  .contact {
    margin-top: 20px;
  }

  .map-frame iframe {
    height: 250px;
  }
}

/* Hover Effects */
footer .social-icon {
  transition: all 0.3s ease;
}

footer .social-icon:hover {
  transform: scale(1.1);
  color: #fff;
}

footer .map-frame iframe {
  transition: transform 0.3s ease;
}

footer .map-frame iframe:hover {
  transform: scale(1.05);
}
</style>

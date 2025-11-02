// Custom Element za e-tickets admin panel
// Sa Sales kao početnom stranicom i modernom animacijom učitavanja

class NavigationWithIframe extends HTMLElement {
  // Početni URL za iframe - postavljen na Sales umjesto Dashboard
  currentUrl = "https://www.e-tickets.me/";
  
  connectedCallback() {
    // Kreiramo osnovnu strukturu
    this.innerHTML = `
      <div class="container" style="display: flex; width: 100vw; height: 100vh; position: fixed; top: 0; left: 0; overflow: hidden; margin: 0; padding: 0;">
        <!-- Fiksni izbornik -->
        <div class="sidebar" style="width: 250px; background-color: #1e1e1e; color: #ebeef2; height: 100vh; overflow-y: auto; position: fixed; left: 0; top: 0; z-index: 1000; font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; transition: transform 0.3s ease;">
          <div class="logo" style="padding: 20px; border-bottom: 1px solid #333; font-weight: 600; font-size: 20px; text-align: center; letter-spacing: 0.5px; color: #0088ff;">
            e-tickets Admin
          </div>
          <ul class="menu" style="list-style: none; padding: 20px 0; margin: 0;">
            <li class="menu-item active" data-url="https://www.e-tickets.me/organizator-dogadjaja" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; background-color: #3a3a3a; border-left: 3px solid #0088ff; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-shopping-basket" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Pregled prodaje</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/pregled" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-chart-line" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Pregled karata</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/adminstat" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-chart-bar" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Statistics</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/ad-events" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-calendar-plus" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Ad Events</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/statistika-skeniranja" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-qrcode" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Skeniranje</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/refund" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-undo-alt" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Povrati/Refund</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/isplate" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-money-bill-wave" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Isplate</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/bukiranje" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-calendar-check" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Booking</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/biletarnica" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-ticket-alt" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Biletarnica</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/biletarnica-1" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-store" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Biletarnica Plus</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/provjera-duplikata" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-copy" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">Provjera duplikata</span>
            </li>
            <li class="menu-item" data-url="https://www.e-tickets.me/cms" style="padding: 14px 20px; cursor: pointer; display: flex; align-items: center; margin-bottom: 5px; transition: all 0.2s ease;">
              <i class="fas fa-cog" style="margin-right: 15px; width: 24px; text-align: center; font-size: 18px;"></i> 
              <span style="font-size: 15px;">CMS</span>
            </li>
          </ul>
          
          <!-- Hamburger meni za mobilne uređaje -->
          <div class="mobile-toggle" style="display: none; position: absolute; top: 15px; right: -45px; width: 40px; height: 40px; background: #1e1e1e; border-radius: 0 5px 5px 0; cursor: pointer; justify-content: center; align-items: center;">
            <i class="fas fa-bars" style="color: #ebeef2; font-size: 20px;"></i>
          </div>
        </div>
        
        <!-- Kontejner za iframe i loader -->
        <div class="content" style="position: fixed; left: 250px; top: 0; right: 0; bottom: 0; overflow: hidden; transition: left 0.3s ease;">
          <!-- Moderna loader animacija -->
          <div id="loader" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; background: #1a1a1a; display: flex; justify-content: center; align-items: center; z-index: 100;">
            <div style="text-align: center;">
              <!-- Moderna circular spinner -->
              <div class="modern-loader" style="position: relative; width: 80px; height: 80px; margin: 0 auto;">
                <!-- Outer rotating circle -->
                <div style="position: absolute; width: 80px; height: 80px; border-radius: 50%; border: 4px solid rgba(0, 136, 255, 0.1); border-top-color: #0088ff; animation: modernSpin 1s cubic-bezier(0.68, -0.55, 0.265, 1.55) infinite;"></div>
                
                <!-- Middle rotating circle -->
                <div style="position: absolute; top: 10px; left: 10px; width: 60px; height: 60px; border-radius: 50%; border: 4px solid rgba(0, 136, 255, 0.1); border-top-color: rgba(0, 136, 255, 0.7); animation: modernSpin 0.8s cubic-bezier(0.68, -0.55, 0.265, 1.55) infinite reverse;"></div>
                
                <!-- Inner pulse circle -->
                <div style="position: absolute; top: 50%; left: 50%; width: 20px; height: 20px; margin: -10px 0 0 -10px; background: #0088ff; border-radius: 50%; animation: pulse 1.5s ease-in-out infinite;"></div>
              </div>
              
              <!-- Loading text sa modernim fontom -->
              <p style="margin-top: 40px; color: #ebeef2; font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif; font-size: 18px; font-weight: 600; letter-spacing: 1px; text-transform: uppercase; opacity: 0.95; animation: fadeInOut 2s ease-in-out infinite;">
                Učitavanje
              </p>
              
              <!-- Animated dots -->
              <div style="display: flex; justify-content: center; gap: 8px; margin-top: 15px;">
                <div style="width: 8px; height: 8px; background: #0088ff; border-radius: 50%; animation: dotFade 1.4s ease-in-out infinite; animation-delay: 0s;"></div>
                <div style="width: 8px; height: 8px; background: #0088ff; border-radius: 50%; animation: dotFade 1.4s ease-in-out infinite; animation-delay: 0.2s;"></div>
                <div style="width: 8px; height: 8px; background: #0088ff; border-radius: 50%; animation: dotFade 1.4s ease-in-out infinite; animation-delay: 0.4s;"></div>
              </div>
            </div>
          </div>
          
          <!-- Iframe za sadržaj -->
          <iframe id="content-frame" style="position: absolute; top: 0; left: 0; width: 100%; height: 100%; border: none; margin: 0; padding: 0; display: none;" src="about:blank" frameborder="0" scrolling="yes"></iframe>
        </div>
      </div>
      
      <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        
        * {
          box-sizing: border-box;
        }
        
        /* Ensure Inter font is applied everywhere */
        body, .sidebar, .menu-item, .logo, p {
          font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif !important;
        }
        
        /* Moderna spinning animacija */
        @keyframes modernSpin {
          0% {
            transform: rotate(0deg);
          }
          100% {
            transform: rotate(360deg);
          }
        }
        
        /* Pulse animacija za unutrašnji krug */
        @keyframes pulse {
          0%, 100% {
            transform: scale(1);
            opacity: 1;
          }
          50% {
            transform: scale(1.3);
            opacity: 0.7;
          }
        }
        
        /* Fade animacija za tekst */
        @keyframes fadeInOut {
          0%, 100% {
            opacity: 0.6;
          }
          50% {
            opacity: 1;
          }
        }
        
        /* Dot fade animacija */
        @keyframes dotFade {
          0%, 100% {
            opacity: 0.3;
            transform: scale(0.8);
          }
          50% {
            opacity: 1;
            transform: scale(1.2);
          }
        }
        
        /* Fade in animacija za iframe */
        @keyframes fadeIn {
          from {
            opacity: 0;
            transform: scale(0.98);
          }
          to {
            opacity: 1;
            transform: scale(1);
          }
        }
        
        .iframe-visible {
          animation: fadeIn 0.5s ease-out;
        }
        
        .menu-item:hover {
          background-color: #2c2c2c !important;
          padding-left: 25px !important;
        }
        
        .menu-item.active:hover {
          background-color: #3a3a3a !important;
        }
        
        .menu-item i {
          transition: transform 0.2s ease;
        }
        
        .menu-item:hover i {
          transform: scale(1.1);
        }
        
        /* Responsive stilovi */
        @media (max-width: 768px) {
          .sidebar {
            transform: translateX(-250px) !important;
          }
          
          .sidebar.open {
            transform: translateX(0) !important;
          }
          
          .mobile-toggle {
            display: flex !important;
          }
          
          .content {
            left: 0 !important;
          }
        }
        
        @media (max-width: 480px) {
          .sidebar {
            width: 200px !important;
          }
          
          .menu-item span {
            font-size: 14px !important;
          }
          
          .sidebar.open + .content {
            transform: translateX(200px);
          }
        }
        
        /* Uklanjamo sve margine i padding-e koji mogu stvarati prazan prostor */
        html, body {
          margin: 0 !important;
          padding: 0 !important;
          overflow: hidden !important;
          width: 100vw !important;
          height: 100vh !important;
        }
      </style>
    `;
    
    // Dodajemo Font Awesome ako već nije dodan
    if (!document.querySelector('link[href*="font-awesome"]')) {
      const fontAwesomeLink = document.createElement('link');
      fontAwesomeLink.rel = 'stylesheet';
      fontAwesomeLink.href = 'https://cdnjs.cloudflare.com/ajax/libs/font-awesome/5.15.3/css/all.min.css';
      document.head.appendChild(fontAwesomeLink);
    }
    
    // Reference na elemente
    const menuItems = this.querySelectorAll('.menu-item');
    const iframe = this.querySelector('#content-frame');
    const loader = this.querySelector('#loader');
    const sidebar = this.querySelector('.sidebar');
    const content = this.querySelector('.content');
    const mobileToggle = this.querySelector('.mobile-toggle');
    
    // Mobile toggle funkcionalnost
    if (mobileToggle) {
      mobileToggle.addEventListener('click', () => {
        sidebar.classList.toggle('open');
        const icon = mobileToggle.querySelector('i');
        if (sidebar.classList.contains('open')) {
          icon.classList.remove('fa-bars');
          icon.classList.add('fa-times');
        } else {
          icon.classList.remove('fa-times');
          icon.classList.add('fa-bars');
        }
      });
    }
    
    // Funkcija za učitavanje URL-a s prikazom loadera
    const loadUrl = (url) => {
      // Prikazujemo loader i sakrivamo iframe
      loader.style.display = 'flex';
      iframe.style.display = 'none';
      iframe.classList.remove('iframe-visible');
      
      // Postavljamo timeout da se optimizira učitavanje
      setTimeout(() => {
        // Učitavamo URL u iframe
        iframe.src = url;
        
        // Postavljamo event listener za učitavanje iframe-a
        iframe.onload = () => {
          // Postavljamo timeout da se iframe stvarno učita
          setTimeout(() => {
            try {
              // Pokušamo pristupiti sadržaju iframe-a za provjeru učitavanja
              const iframeDoc = iframe.contentDocument || iframe.contentWindow.document;
              
              // Ako je stranica učitana, sakrivamo loader
              if (iframeDoc.readyState === 'complete' || iframeDoc.readyState === 'interactive') {
                loader.style.display = 'none';
                iframe.style.display = 'block';
                iframe.classList.add('iframe-visible');
              } else {
                // Ako stranica nije učitana, provjeravamo ponovo za 500ms
                setTimeout(() => {
                  loader.style.display = 'none';
                  iframe.style.display = 'block';
                  iframe.classList.add('iframe-visible');
                }, 500);
              }
            } catch (e) {
              // U slučaju CORS greške (cross-origin), ne možemo pristupiti sadržaju
              // Ali ipak prikazujemo iframe nakon 1 sekunde
              setTimeout(() => {
                loader.style.display = 'none';
                iframe.style.display = 'block';
                iframe.classList.add('iframe-visible');
              }, 1000);
            }
          }, 800);
        };
        
        // Error handling
        iframe.onerror = () => {
          console.error('Greška pri učitavanju stranice:', url);
          loader.style.display = 'none';
          iframe.style.display = 'block';
          
          // Dispatch error event
          this.dispatchEvent(new CustomEvent('loadError', {
            detail: { url: url, error: 'Failed to load page' },
            bubbles: true,
            composed: true
          }));
        };
      }, 50);
      
      // Sigurnosni timeout - prikazati iframe nakon max 5 sekundi
      setTimeout(() => {
        if (loader.style.display !== 'none') {
          loader.style.display = 'none';
          iframe.style.display = 'block';
          iframe.classList.add('iframe-visible');
        }
      }, 5000);
    };
    
    // Učitavamo početni URL (Sales)
    loadUrl(this.currentUrl);
    
    // Dodajemo event listenere za stavke izbornika
    menuItems.forEach(item => {
      item.addEventListener('click', () => {
        // Uklanjamo aktivnu klasu sa svih stavki
        menuItems.forEach(i => {
          i.classList.remove('active');
          i.style.backgroundColor = '';
          i.style.borderLeft = '';
        });
        
        // Dodajemo aktivnu klasu na kliknutu stavku
        item.classList.add('active');
        item.style.backgroundColor = '#3a3a3a';
        item.style.borderLeft = '3px solid #0088ff';
        
        // Na mobilnim uređajima zatvaramo meni nakon klika
        if (window.innerWidth <= 768) {
          sidebar.classList.remove('open');
          const icon = mobileToggle.querySelector('i');
          icon.classList.remove('fa-times');
          icon.classList.add('fa-bars');
        }
        
        // Uzimamo URL iz data atributa
        const url = item.getAttribute('data-url');
        this.currentUrl = url;
        
        // Učitavamo URL u iframe s animacijom
        loadUrl(url);
        
        // Šaljemo event da je promijenjen URL
        this.dispatchEvent(new CustomEvent('navigate', {
          detail: {
            url: url,
            name: item.querySelector('span').textContent.trim()
          },
          bubbles: true,
          composed: true
        }));
      });
    });
    
    // Funkcija za prilagođavanje veličine
    const handleResize = () => {
      // Provjeravamo da li treba prikazati/sakriti mobilni toggle
      if (window.innerWidth > 768 && sidebar.classList.contains('open')) {
        sidebar.classList.remove('open');
        const icon = mobileToggle.querySelector('i');
        icon.classList.remove('fa-times');
        icon.classList.add('fa-bars');
      }
    };
    
    // Pozovi resize odmah i na svaku promjenu veličine
    handleResize();
    window.addEventListener('resize', handleResize);
    
    // Očisti event listener kad se element ukloni
    this.disconnectCallback = () => {
      window.removeEventListener('resize', handleResize);
    };
    
    // Šaljemo event da je element spreman
    this.dispatchEvent(new CustomEvent('ready', {
      detail: {
        initialUrl: this.currentUrl
      },
      bubbles: true,
      composed: true
    }));
  }
  
  disconnectedCallback() {
    // Očisti event listenere
    if (this.disconnectCallback) {
      this.disconnectCallback();
    }
  }
  
  // Metoda za promjenu URL-a iz Velo koda
  setUrl(url) {
    if (url) {
      this.currentUrl = url;
      
      // Reference na elemente
      const iframe = this.querySelector('#content-frame');
      const loader = this.querySelector('#loader');
      
      // Prikazujemo loader i učitavamo URL
      loader.style.display = 'flex';
      iframe.style.display = 'none';
      iframe.classList.remove('iframe-visible');
      
      // Učitavamo URL s unapređenim loaderom
      setTimeout(() => {
        iframe.src = url;
        
        iframe.onload = () => {
          // Dajemo stranici više vremena da se učita
          setTimeout(() => {
            try {
              const iframeDoc = iframe.contentDocument || iframe.contentWindow.document;
              
              if (iframeDoc.readyState === 'complete' || iframeDoc.readyState === 'interactive') {
                loader.style.display = 'none';
                iframe.style.display = 'block';
                iframe.classList.add('iframe-visible');
              } else {
                setTimeout(() => {
                  loader.style.display = 'none';
                  iframe.style.display = 'block';
                  iframe.classList.add('iframe-visible');
                }, 500);
              }
            } catch (e) {
              setTimeout(() => {
                loader.style.display = 'none';
                iframe.style.display = 'block';
                iframe.classList.add('iframe-visible');
              }, 1000);
            }
          }, 800);
        };
        
        // Error handling
        iframe.onerror = () => {
          console.error('Greška pri učitavanju stranice:', url);
          loader.style.display = 'none';
          iframe.style.display = 'block';
          
          this.dispatchEvent(new CustomEvent('loadError', {
            detail: { url: url, error: 'Failed to load page' },
            bubbles: true,
            composed: true
          }));
        };
      }, 50);
      
      // Sigurnosni timeout
      setTimeout(() => {
        if (loader.style.display !== 'none') {
          loader.style.display = 'none';
          iframe.style.display = 'block';
          iframe.classList.add('iframe-visible');
        }
      }, 5000);
      
      // Ažuriramo aktivnu stavku u izborniku
      const menuItems = this.querySelectorAll('.menu-item');
      menuItems.forEach(item => {
        const itemUrl = item.getAttribute('data-url');
        if (itemUrl === url) {
          item.classList.add('active');
          item.style.backgroundColor = '#3a3a3a';
          item.style.borderLeft = '3px solid #0088ff';
        } else {
          item.classList.remove('active');
          item.style.backgroundColor = '';
          item.style.borderLeft = '';
        }
      });
    }
  }
  
  // Getter za trenutni URL
  getUrl() {
    return this.currentUrl;
  }
}

// Registracija custom elementa
customElements.define('navigation-with-iframe', NavigationWithIframe);

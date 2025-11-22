<template>
  <footer class="footer">
    <div class="container">
      <!-- NAV BLOCK -->
      <nav class="footer__nav" aria-label="Footer navigation">
        <div v-for="group in footerGroups" :key="group.title" class="footer__column">
          <h3 class="footer__title">
            {{ group.title }}
          </h3>
          <ul class="footer__list">
            <li v-for="link in group.links" :key="link.label" class="footer__item">
              <a class="footer__link" :href="link.href">
                {{ link.label }}
              </a>
            </li>
          </ul>
        </div>
      </nav>

      <!-- BOTTOM BLOCK -->
      <div class="footer__bottom">
        <div class="footer__brand">
          <img src="@/assets/logo.png" alt="Aston VIP" class="footer__logo" />

          <div class="footer__social">
            <span class="footer__social-label">Follow us</span>
            <div class="footer__social-icons">
              <a href="https://instagram.com" target="_blank" aria-label="Instagram">
                <img src="/icons/instagram.svg" alt="Instagram" />
              </a>
              <a href="https://linkedin.com" target="_blank" aria-label="LinkedIn">
                <img src="/icons/linkedin.svg" alt="LinkedIn" />
              </a>
              <a href="https://facebook.com" target="_blank" aria-label="Facebook">
                <img src="/icons/facebook.svg" alt="Facebook" />
              </a>
            </div>
          </div>
        </div>

        <div v-for="office in offices" :key="office.country" class="footer__office">
          <img v-if="office && office?.img" :src="office.img" alt="office" />
          <div class="footer__office-country">
            {{ office.country }}
          </div>
          <div class="footer__office-text">
            <p>{{ office.address }}</p>
            <p>{{ office.schedule }}</p>
            <p>
              <a :href="`tel:${office.phone}`">{{ office.phone }}</a>
            </p>
            <p>
              <a :href="`mailto:${office.email}`">{{ office.email }}</a>
            </p>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script setup>
const footerGroups = [
  {
    title: 'Business setup',
    links: [
      { label: 'Business setup', href: '/' },
      { label: 'IFZA', href: '/' },
      { label: 'DMCC', href: '/' },
      { label: 'Mainland', href: '/' },
      { label: 'Free Zones', href: '/' },
    ],
  },
  {
    title: 'Personal services',
    links: [
      { label: 'Dubai residence VISA (VIP)', href: '/' },
      { label: 'Dubai relocation services', href: '/' },
      { label: 'International school in Dubai', href: '/' },
      { label: 'Property search in Dubai', href: '/' },
      { label: 'Drivers license in Dubai', href: '/' },
    ],
  },
  {
    title: 'Advisory services',
    links: [
      { label: 'Accounting and bookkeeping services', href: '/' },
      { label: 'Audit', href: '/' },
      { label: 'VAT', href: '/' },
      { label: 'TAX consultancy', href: '/' },
      { label: 'Legal', href: '/' },
      { label: 'VIP', href: '/' },
    ],
  },
  {
    title: 'Trust funds',
    links: [
      { label: 'UAE Trust', href: '/' },
      { label: 'Cyprus Trust', href: '/' },
    ],
  },
  {
    title: 'Crypto',
    links: [
      { label: 'Crypto company setup in Dubai', href: '/' },
      { label: 'VARA license', href: '/' },
    ],
  },
  {
    title: 'Commodities',
    links: [
      { label: 'Oil and fuel', href: '/' },
      { label: 'Gold trade', href: '/' },
    ],
  },
  {
    title: 'Financial services',
    links: [
      { label: 'Open company bank account in Dubai', href: '/' },
      { label: 'Large cash transactions', href: '/' },
      { label: 'Open private bank account in Dubai', href: '/' },
      { label: 'Card services in Dubai', href: '/' },
      { label: 'Corporate banking', href: '/' },
      { label: 'Standard business bank account', href: '/' },
      { label: 'SME bank account', href: '/' },
      { label: 'Business gold account', href: '/' },
      { label: 'High-risk bank accounts', href: '/' },
      { label: 'Invoicing, tax savings & fast transfers', href: '/' },
      { label: 'Open local account in DKK, EUR, GBP', href: '/' },
    ],
  },
  {
    title: 'Resources',
    links: [
      { label: 'About us', href: '/' },
      { label: 'Contact us', href: '/' },
      { label: 'Blog', href: '/' },
      { label: 'Guide: Banking in Dubai 2025', href: '/' },
      { label: 'Guide: Choosing company location in Dubai 2025', href: '/' },
      { label: 'Guide: How to get a VARA licence in Dubai 2025', href: '/' },
      { label: 'Guide: Company setups and corporate banking in Switzerland', href: '/' },
    ],
  },
  {
    title: 'Legal',
    links: [
      { label: 'Privacy policy', href: '/' },
      { label: 'Cookies policy', href: '/' },
      { label: 'Terms and conditions', href: '/' },
      { label: 'Anti-Money Laundering (AML) Policy', href: '/' },
      {
        label: 'General data protection regulation (GDPR) compliance for Aston VIP',
        href: '/',
      },
      { label: 'Know Your Customer (KYC) Policy', href: '/' },
    ],
  },
]

const offices = [
  {
    country: 'United Kingdom',
    address: '128 City Road - London',
    schedule: 'Mon-Fri (9 AM - 6 PM)',
    phone: '+44 20805 08084',
    email: 'contact@aston.ae',
    img: './icons/office.png',
  },
  {
    country: 'United Arab Emirates',
    address: 'Cluster W, JLT - Dubai',
    schedule: 'Mon-Fri (9 AM - 6 PM)',
    phone: '+971 4 518 2623',
    email: 'contact@aston.ae',
    img: './icons/office-dub.png',
  },
]
</script>

<style scoped lang="scss">
.footer {
  background: $black;
  color: $white-color;
  padding: 90px 0 90px;
}

/* NAV GRID */
.footer__nav {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 40px 56px;
  @media (max-width: 1200px) {
  }
  @media (max-width: 768px) {
    grid-template-columns: 1fr 1fr;
    gap: 40px 16px;
  }
  @media (max-width: 400px) {
    grid-template-columns: 1fr;
    gap: 30px 16px;
  }
}

.footer__column {
  min-width: 0;
}

.footer__title {
  font-size: 20px;
  font-weight: 700;
  margin-bottom: 16px;
  padding-bottom: 12px;
  border-bottom: 1px solid $small-text;
}

.footer__list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.footer__item + .footer__item {
  margin-top: 16px;
}

.footer__link {
  color: $black-200;
  text-decoration: none;
  line-height: 1.5;
  transition: color 0.5s ease;

  &:hover {
    color: #ff6000;
  }
}

/* BOTTOM */
.footer__bottom {
  margin-top: 72px;
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 40px 56px;
  @media (max-width: 1200px) {
  }
  @media (max-width: 768px) {
    margin-top: 72px;
    display: flex;
    gap: 40px;
    justify-content: space-between;
    align-items: flex-start;
    flex-wrap: wrap;
  }

}

/* LEFT SIDE: logo + social */
.footer__brand {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 18px;
  min-width: 125px;
  @media (max-width: 768px) {
    order: 1;
    width: 100%;
    flex-direction: row;
    justify-content: space-around;
  }
}

.footer__logo {
  height: 100px;
  width: 100px;
}

.footer__social-label {
  font-size: 14px;
  text-transform: uppercase;
  color: #ffffff;
  display: flex;
  justify-content: center;
}

.footer__social-icons {
  margin-top: 16px;
  display: flex;
  gap: 16px;

  img {
    width: 24px;
    height: 24px;
    display: block;
    transition: transform 0.5s ease;
  }

  a:hover img {
    transform: scale(1.08);
  }
}

/* RIGHT SIDE: offices */

.footer__office {
  display: flex;
  flex-direction: column;
  gap: 16px;
  color: $black-200;
  img {
    height: 100px;
    width: 100px;
  }
  @media (max-width: 768px) {
    max-width: calc(50% - 20px);
  }
}

.footer__office-country {
  text-transform: uppercase;
  letter-spacing: 0.08em;
  font-size: 14px;
  color: #ffffff;
}

.footer__office-text p {
  margin: 0 0 4px;
}

.footer__office-text a {
  color: $black-200;
  transition: color 0.5s ease;

  &:hover {
    color: #ff6000;
  }
}

/* RESPONSIVE */
@media (max-width: 768px) {
  //.footer {
  //  padding: 40px 0 28px;
  //}

  //.footer__bottom {
  //  flex-direction: column;
  //  gap: 24px;
  //}

  //.footer__brand {
  //  align-items: flex-start;
  //}
}
</style>

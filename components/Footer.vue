<template>
  <footer class="footer">
    <div class="content">
      <div class="footer-content-wrapper">
        <div class="footer-copy">
          <div class="copyright"></div>
          <div class="rights"></div>
          <div class="footer__socials-container"></div>
          <div class="footer-langs"></div>
        </div>
        <div class="footer-links">
          <div class="footer-links-column">
            <div class="footer-links-title"></div>
            <a href=""></a>
          </div>
          <div class="footer-links-column">
            <div class="footer-links-title"></div>
            <a href=""></a>
          </div>
        </div>
        <div class="footer-text">
          <div class="footer-text-title"></div>
          <div class="footer-text-p"></div>
          <a href="/account/login" class="btn"></a>
        </div>
      </div>
    </div>
  </footer>
</template>


<script>
export default {
  computed: {
    lang() {
      return this.$store.getters.lang
    },
  },
  data() {
    return {
      isMenuActivated: {
        lang: false,
      },
    }
  },
  methods: {
    closeAll() {
      this.isMenuActivated.lang = false
    },
    toggleLangMenu() {
      this.isMenuActivated.lang = !this.isMenuActivated.lang
    },
    setLang(lang) {
      if (this.$route.params.lang !== lang) {
        this.$store.commit('SET_LANG', lang)
        const toLang = this.$route.params.lang
        const path = this.$nuxt.$route.path.replace(toLang, lang)
        this.$i18n.setLocale(lang)
        localStorage.setItem('lang', lang)
        this.$router.push({path: path})
      }
    },

    removeHandlers() {
      document.body.removeEventListener('click', this.closeAll)
    },

    addHandlers() {
      document.body.addEventListener('click', this.closeAll)
    },
  }
}
</script>

<style scoped lang='scss'>
.footer {
  padding: 65px 0 77px;
  border-top: 1px solid #D9D9D9;
}
.footer-content-wrapper {
  display: flex;
  justify-content: space-between;
}
.footer-copy {
  width: 24%;
}
.copyright {
  font-size: 15px;
  color: #29292D;
  margin-bottom: 13px;
}
.rights {
  font-size: 14px;
  color: #B4B4C2;
  margin-bottom: 22px;
}
.footer-langs {
  position: relative;
  display: inline-block;
}
.footer-langs-btn {
  font-size: 14px;
  width: 98px;
  height: 46px;
  border: 1px solid #B4C0DB;
  border-radius: 5px;
  padding: 5px 17px 5px;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.footer-links {
  display: flex;
  justify-content: space-around;
  width: 43%;
}
.footer-links-column {
  display: flex;
  flex-direction: column;
}
.footer-links-column a {
  color: #42A4FF;
  font-size: 16px;
  margin-bottom: 16px;
  font-weight: 500;
}
.footer-links-title {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 21px;
}
.footer-text {
  width: 24%;
}
.footer-text-title {
  font-size: 18px;
  font-weight: 700;
  margin-bottom: 9px;
}
.footer-text-p {
  font-size: 14px;
  margin-bottom: 19px;
}
.btn {
  padding: 15px 30px;
}
.navigation-language {
  display: none;
  position: absolute;
  top: 51px;
  left: 0;
  border: 1px solid #B4C0DB;
  width: 100%;
  padding: 10px 20px;
  border-radius: 5px;
}
.navigation-language__link {
  color: #000;
  text-transform: capitalize;
  cursor: pointer;
  display: block;
  padding: 4px 0;
}
.navigation-language.active {
  display: block;
}

@media (max-width: 900px) {
  .footer-content-wrapper {
    display: flex;
    flex-direction: column;
  }
  .footer {
    padding: 26px 0 29px;
  }
  .footer-links {
    order: -1;
  }
  .footer-links {
    flex-wrap: wrap;
    width: 100%;
  }
  .footer-links-column {
    width: 50%;
  }
  .footer-links-column a {
    font-size: 12px;
    margin-bottom: 14px;
  }
  .footer-links-title {
    font-size: 16px;
    margin-bottom: 9px;
  }
  .footer-text {
    width: 100%;
    order: -1;
    padding-top: 16px;
  }
  .footer-copy {
    width: 100%;
    padding-top: 30px;
  }
  .footer-text-p {
    font-size: 12px;
    margin-bottom: 10px;
  }
  .copyright {
    font-size: 12px;
  }
  .footer-langs-btn {
    font-size: 13px;
    width: 71px;
    height: 38px;
    border: 1px solid #B4C0DB;
    border-radius: 5px;
    padding: 5px 9px 5px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }
  .rights {
    font-size: 12px;
  }
}
.footer-langs {
  display: none !important;
}
.footer__socials-container {
  display: flex;
  flex-wrap: wrap;
}
.footer__social-item {
  width: 40%;
  padding-right: 10px;
  color: #42a4ff;
  white-space: nowrap;
}
.footer__social-item span {
  width: 20px;
  height: 15px;
  display: inline-block;
  text-align: center;
  margin-left: -5px;
}
</style>

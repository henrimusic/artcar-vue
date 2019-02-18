<template>    
    <b-navbar toggleable="lg" type="dark" id="nav">
    <b-navbar-brand href="#"><img class="logo-nav" src="../../../assets/img/artcar-logo.png" alt></b-navbar-brand>

      <b-navbar-toggle target="nav_collapse" />
      
      <b-collapse is-nav id="nav_collapse">
       
        <b-navbar-nav class="ml-auto">
          <b-nav-item class="link-desk"><router-link class="link-1" :to="{name: 'home'}">Home</router-link>
          </b-nav-item>
          <b-nav-item  class="link-desk"><router-link class="link-1" :to="{name: 'veiculos'}">Veiculos</router-link>
          </b-nav-item>
          <b-nav-item  class="link-desk"><router-link class="link-1" :to="{name: 'contato'}">Contato</router-link>
        </b-nav-item>
        </b-navbar-nav>
        
      </b-collapse>
        
    </b-navbar>
</template>

<script>
export default {
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed () {
    window.removeEventListener('scroll', this.handleScroll);
  },
  methods: {
    handleScroll() {
      window.scrollY > 100 ? 
        document.getElementById('nav').classList.add('bg-color-2') :
        document.getElementById('nav').classList.remove('bg-color-2')
    }
  }
};
</script>


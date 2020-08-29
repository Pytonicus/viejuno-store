<template>
  <div id="app">
    <HeaderComponent />
    <NavComponent />
    <MontaMaquinaPage />
    <FooterComponent />
  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue';
import NavComponent from './components/NavComponent.vue';
import MontaMaquinaPage from './components/MontaMaquinaPage.vue';
import FooterComponent from './components/FooterComponent.vue';


export default {
  name: 'App',
  components: {
    HeaderComponent,
    NavComponent,
    MontaMaquinaPage,
    FooterComponent
  }
}
</script>

<style> 
@import './assets/css/styles.css';
</style>

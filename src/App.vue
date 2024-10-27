<script setup>
import { ref } from 'vue';
import CV_Header from './components/CV_Header.vue';
import CV_Contact from './components/CV_Contact.vue';
import { FontAwesomeIcon } from '@fortawesome/vue-fontawesome'
import CV_Part from './components/CV_Part.vue';
const parts = ref([
  { id: 1, title: 'Diplomes et formations', displayed: false },
  { id: 2, title: 'Expériences et projets', displayed: false },
  { id: 3, title: 'Références et recommandations', displayed: false }
])
</script>

<template>
<div class="container">
  <div class="partie partie1">
      <div class="left-part">
        <CV_Header>
          <template #name>
            <h1>Nicolas VIALLON</h1>
          </template>
          <template #job>
            <h2>Développeur Junior</h2>
          </template>
          <template #catchphrase>
            <h3>Diplômé en développement, je suis à la recherche d'un emploi dans
            ce milieu qui me passionne. Impliqué et motivé, je souhaite acquérir
            de l'expérience et des responsabilités afin de m'épanouir dans ma
            carrière professionnelle. Je suis disponible immédiatement !</h3>
          </template>
        </CV_Header>
        <CV_Part
          v-for="part in parts"
          :key="part.id"
          :id="part.id"
          :title="part.title"
          :displayed="part.displayed"
          :loading="false"
          :active="false"
          @activated="console.log('activé')"
          @deactivated="console.log('desactivé')"
        />
      </div>
  </div>
  <div class="liseret"></div>
  <div class="partie partie2">
      <div class="right-part">
        <CV_Contact>
          <template #email>
            <!-- Add the style and icon you want using the Array format -->
            <font-awesome-icon :icon="['fas', 'user-secret']" />
            <span class="contact">viallon.nicolas@gmail.com</span>
          </template>
          <template #localisation>
            <FontAwesomeIcon icon="fa-brands fa-twitter" />
            <span class="contact">9 route de manom</span>
          </template>
        </CV_Contact>
      </div>
  </div>
</div>
  
  
</template>

<style scoped>
  body {
      font-family: Arial, sans-serif;
      margin: 0;
      padding: 0;
  }
  .container {
      display: flex;
      flex-direction: row;
      height: auto;
  }
  .partie {
      flex: 1;
      padding: 20px;
  }
  .partie1 {
      flex: 2;
      background-color: #f0f8ff;
  }
  .partie2 {
      background-color: #353535;
      color: white;
  }
  .liseret {
      width: 1px;
      background-color: #000;
      margin: 0;
  }
  .contact {
    margin-left: 10px;
  }
</style>
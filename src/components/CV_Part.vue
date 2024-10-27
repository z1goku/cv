<script setup>
import Part_item from './Part_item.vue';
import { ref } from 'vue';
import Button_item from './Button_item.vue';
const active = ref(false);
const props = defineProps(['id', 'title', 'displayed', 'loading', 'active']);
const emits = defineEmits(['activated', 'deactivated']);
const count = ref(0);
const displayChange = () => {
    document.getElementsByClassName('pong-container')[props.id-1].style.display = 'block';
    active.value = !active.value;
    if (active.value) {
      emits('activated');
      setTimeout(function() {
        // Cacher le loader et afficher la div principale
        document.getElementsByClassName('pong-container')[props.id-1].style.display = 'none';
        document.getElementsByClassName('maDiv')[props.id-1].style.display = 'block'; // Afficher la div
    }, 1000); // 3000 millisecondes = 3 secondes
    }
    else {
      emits('deactivated');
      setTimeout(function() {
        // Cacher le loader et afficher la div principale
        document.getElementsByClassName('pong-container')[props.id-1].style.display = 'none';
        document.getElementsByClassName('maDiv')[props.id-1].style.display = 'none'; // Afficher la div
    }, 1000); // 3000 millisecondes = 3 secondes
    }
    console.log('madiv' + props.id)

}
</script>
<template v-if="props.title">
    <h1>{{ title }}</h1>
    <Button_item @click="displayChange"><strong>Afficher</strong></Button_item>
    <div class="pong-container">
      <div class="pong-paddle"></div>
    </div>
    <div class="maDiv">
        <Part_item>
          <template #title_item>
            <span><strong>Titre</strong></span>
          </template>
          <template #desc_item>
            <span>Description</span>
          </template>
        </Part_item>
    </div>
</template>
<style>
  .loader {
      display: none; /* Cacher le loader au départ */
      border: 4px solid #f3f3f3; /* Couleur de fond */
      border-top: 4px solid #3498db; /* Couleur de la barre */
      border-radius: 50%; /* Forme ronde */
      width: 40px; /* Largeur du loader */
      height: 40px; /* Hauteur du loader */
      animation: spin 1s linear infinite; /* Animation de rotation */
      margin: 10px auto; /* Centrer le loader */
  }

  @keyframes spin {
      0% { transform: rotate(0deg); }
      100% { transform: rotate(360deg); }
  }

  .maDiv {
      display: none; /* Cacher la div au départ */
      background-color: lightblue;
      padding: 20px;
      margin: 10px 0;
  }
  .pong-container {
    display: none; 
    width: 300px;
    height: 10px; /* Hauteur du conteneur */
    background-color: #e0e0e0; /* Couleur de fond */
    position: relative; /* Nécessaire pour le positionnement de la raquette */
    overflow: hidden; /* Masque le débordement */
  }
  .pong-paddle {
      width: 100px; /* Largeur de la raquette */
      height: 10px; /* Hauteur de la raquette */
      background-color: #0073b1; /* Couleur de la raquette */
      /*background: linear-gradient(to right,rgba(0, 115, 177, 0) 0%, rgba(0, 115, 177, 1) 20%);*/
      position: absolute; /* Positionnement absolu */
      animation: movePaddle 1s ease-in-out infinite; /* Animation de la raquette */
  }
  @keyframes movePaddle {
      0% {
          left: 0px; /* Départ à gauche */ 
          width: 100px;
          transform: scaleX(1);
      }
      50% {
          left: 250px;
          transform: scaleX(2);
      }
      100% {
          left: -0px;
          width: 100px;
          transform: scaleX(1);
          }
  }
</style>


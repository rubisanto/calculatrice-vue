<script setup>
import { RouterLink, RouterView } from 'vue-router'
import myHeader from './components/myHeader.vue'
import myFooter from './components/myFooter.vue'
import mySlot from './components/mySlot.vue'
import myButton from './components/myButton.vue'


</script>

<template>
  <myHeader/>
  <main>
    <!-- affiche le résultat dans mySlot -->
    <mySlot v-text="result"/>
    <!-- input nombre 1 , au changement faire une méthode "verifNumber"-->
    <input type="number" v-model="nombre1" placeholder="nombre 1" v-bind:class="nb1Color" @change="verifNumber1"/>


    <!-- input nombre 2  -->
    <input type="number" v-model="nombre2" placeholder="nombre 2" v-bind:class="nb2Color" @change="verifNumber2">

    <!-- affiche les boutons -->
    <myButton @click="addition" text="addition"/>
    <myButton @click="soustraction" text="soustraction"/>
    <myButton @click="multiplication" text="multiplication"/>
    <myButton @click="division" text="division"/>


  </main>
  <myFooter/>
</template>

<script>

export default {
  name: 'App',
  data() {
    return {
      nombre1: '',
      nombre2: '',
      result: '',
      nb1Color: 'bordure-rouge',
      nb2Color: 'bordure-rouge'
    }
  },
  methods: {
    addition() {
      this.result= parseInt(this.nombre1) + parseInt(this.nombre2)
    },
    soustraction() {
      this.result= parseInt(this.nombre1) - parseInt(this.nombre2)
    },
    multiplication() {
      this.result= parseInt(this.nombre1) * parseInt(this.nombre2)
    },
    division() {
      // si nombre 2 différent de 0


      if(this.nombre2 != 0) this.result= parseInt(this.nombre1) / parseInt(this.nombre2)
    },
    verifNumber1() {
      if (isNaN(this.nombre1)) {
        // donner la classe bordure-rouge à l'input nombre 1
        // mettre nb1Color à bordure-rouge
        this.nb1Color = 'bordure-rouge'
        
      }else {
        // donner la classe bordure-verte à l'input nombre 1
        // mettre nb1Color à bordure-verte
        this.nb1Color = 'bordure-verte'
       
      }
    },
    verifNumber2() {
      if (isNaN(this.nombre2)) {
        // donner la classe bordure-rouge à l'input nombre 2
        this.nb2Color = 'bordure-rouge'

        
      }else {
        // donner la classe bordure-verte à l'input nombre 2
        this.nb2Color = 'bordure-verte'
        
      }
    }
  }
}

</script>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

.bordure-verte {
  border: 2px solid green;
}

.bordure-rouge {
  border: 2px solid red;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}


</style>

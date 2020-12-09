<template>
  <div id="app">
    <header>
      <nav class="navbar navbar-expand-md navbar-light bg-light">
        <a class="navbar-brand" href="#">
          <img 
          src="https://bootstrap-4.ru/docs/4.5/assets/brand/bootstrap-solid.svg" 
          width="30" height="30" 
          srcset="https://bootstrap-4.ru/docs/4.5/assets/brand/bootstrap-solid.svg 300w,
                  ./assets/logo.png 200w"
          sizes="(max-width: 200px) 150px,
                  800px"        
          class="d-inline-block align-top anime" 
          alt="logo">
          Makarov
        </a>

        <button class="navbar-toggler" type="button" data-toggle="collapse" data-target="#navbarSupportedContent" aria-controls="navbarSupportedContent" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>

        <div class="collapse navbar-collapse" id="navbarSupportedContent">
          <ul class="navbar-nav ml-auto">
            <li :class="{'active': home, 'nav-item': true}">
              <span @click="showHome()" class="nav-link" role="button">Home</span>
            </li>
            <li :class="{'active': cpu, 'nav-item': true}">
              <span @click="showCPU()" class="nav-link" role="button">Prosucts CPU</span>
            </li>
            <li :class="{'active': mb, 'nav-item': true}">
              <span @click="showMB()" class="nav-link" role="button">Prosucts MB</span>
            </li>
          </ul>
        </div>
      </nav>
    </header>

    <main class="container">
      <transition name="fade" mode="in-out">
        <HOME v-if="home" />
        <CPU v-if="cpu" />
        <MBS v-if="mb" />
      </transition>
    </main>


  </div>
</template>

<script>
import HOME from "./components/home";
import CPU from "./components/cpus";
import MBS from "./components/mbs";
export default {
  name: 'App',
  data() {
    return {
      home: true,
      cpu: false,
      mb: false
    }
  },
  components: {
    CPU, HOME, MBS
  },
  methods: {
    showHome() {
      this.home = true,
      this.cpu = false,
      this.mb = false
    },
    showCPU() {
      this.home = false,
      this.cpu = true,
      this.mb = false
    },
    showMB() {
      this.home = false,
      this.cpu = false,
      this.mb = true
    }
  },
}
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s;
}
.fade-enter, .fade-leave-to /* .fade-leave-active до версии 2.1.8 */ {
  opacity: 0;
}
* {
  font-family: 'Andika New Basic', sans-serif;
}
body {
  background: #fdfcfc;
}
.anime {
  animation: anime 2s infinite;
}

@keyframes anime {
  0% {transform: translate(0, 0);}
  25% {transform: translate(2000%, 0);}
  50% {transform: translate(1000%, 0);}
  75% {transform: translate(3000%, 0);}
  100% {transform: translate(0, 0);}
}
</style>

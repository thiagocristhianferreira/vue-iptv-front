<template>
  <div id="app">
    <div id="nav" class="botões">
      <router-link to="/">HOME</router-link>
      <h2>{{ titulo }}</h2>
      <div class="save">
        <Toggle v-on:background="mudaTitulo" />
      </div>
    </div>
    <router-view />
  </div>
</template>

<script>
import Toggle from './components/Toogle.vue';

export default {
  name: 'app',
  components: {
    Toggle,
  },
  data() {
    return {
      titulo: 'Dark Mode',
      background: 'black',
      letra: 'white',
    };
  },
  mounted() {
    this.setBackGround('black', 'white');
  },
  methods: {
    setBackGround() {
      const getBody = document.getElementById('app');
      getBody.style.setProperty('background', this.background);
      getBody.style.setProperty('color', this.letra);
    },
    mudaTitulo(payload) {
      if (payload === 'white') {
        this.titulo = 'Light Mode';
        this.background = 'white';
        this.letra = 'black';
        this.setBackGround();
      } else {
        this.titulo = 'Dark Mode';
        this.background = 'black';
        this.letra = 'white';
        this.setBackGround();
      }
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;
  display: flex;
  justify-content: space-between;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}

svg {
  margin-left:10px;
}

.botões {
  display: flex;
  align-items: center;
}

.save {
  display: flex;
}
</style>

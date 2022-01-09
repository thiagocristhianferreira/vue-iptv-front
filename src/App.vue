<template>
  <div id="app">
    <div id="nav" class="botões">
      <router-link to="/">HOME</router-link>
      <h2>{{titulo}}</h2>
      <div class="save">
        <Toggle v-on:background="mudaTitulo"/>
        <!-- <button
          class="btn btn-primary ml-2"
        >
          <svg
            v-on:click="save"
            width=35px
            aria-hidden="true"
            focusable="false"
            data-prefix="far"
            data-icon="save"
            class="svg-inline--fa fa-save fa-w-14"
            role="img"
            xmlns="http://www.w3.org/2000/svg" viewBox="0 0 448 512"><path fill="currentColor" d="M433.941 129.941l-83.882-83.882A48 48 0 0 0 316.118 32H48C21.49 32 0 53.49 0 80v352c0 26.51 21.49 48 48 48h352c26.51 0 48-21.49 48-48V163.882a48 48 0 0 0-14.059-33.941zM272 80v80H144V80h128zm122 352H54a6 6 0 0 1-6-6V86a6 6 0 0 1 6-6h42v104c0 13.255 10.745 24 24 24h176c13.255 0 24-10.745 24-24V83.882l78.243 78.243a6 6 0 0 1 1.757 4.243V426a6 6 0 0 1-6 6zM224 232c-48.523 0-88 39.477-88 88s39.477 88 88 88 88-39.477 88-88-39.477-88-88-88zm0 128c-22.056 0-40-17.944-40-40s17.944-40 40-40 40 17.944 40 40-17.944 40-40 40z"></path></svg>
        </button> -->
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
      titulo: 'Light Mode',
      background: 'white',
    };
  },
  // computed() {
  //   // const back = localStorage.getItem('backgroundMode');
  //   // const getButton = document.querySelector('#toggle');
  //   // if (back === 'black') {
  //   //   this.background = back;
  //   //   console.log('black');
  //   //   setTimeout(() => {
  //   //     document.querySelector('.toggle-wrapper').dispatchEvent(new CustomEvent('click'));
  //   //     console.log(getButton);
  //   //   }, 1000);
  //   //   this.mudaTitulo('black');
  //   // }
  //   return {
  //     teste: () => this.toggle(),
  //   };
  // },
  methods: {
    mudaTitulo(payload) {
      const getBody = document.getElementById('app');
      if (payload === 'white') {
        this.titulo = 'Light Mode';
        getBody.style.setProperty('background', 'white');
        this.background = 'white';
      } else {
        this.titulo = 'Dark Mode';
        getBody.style.setProperty('background', 'black');
        this.background = 'black';
      }
    },
    save() {
      localStorage.setItem('backgroundMode', this.background);
    },
    toggle() {
      if (this.background === 'dark') {
        this.background = 'light';
        const getBody = document.getElementById('app');
        getBody.style.setProperty('background', 'black');
        this.$emit('background', 'black');
      } else {
        this.background = 'dark';
        const getBody = document.getElementById('app');
        getBody.style.setProperty('background', 'black');
        this.$emit('background', 'black');
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

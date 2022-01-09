<template>
  <div class="home">
    <ul style="list-style: none;">
      <li v-for="(link, index) in LINKS" v-bind:key="index">
          <a v-bind:href=link.lk target="_blank">
            <button type="button" class="btn btn-primary mb-2">{{link.canal}}</button>
          </a>
      </li>
    </ul>
  </div>
</template>

<script>
import LINKS from '../links/links';

export default {
  name: 'Home',
  components: {
  },
  data() {
    return { LINKS };
  },
};
</script>

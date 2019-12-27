<template>
  <div id="app">
    <h1>受信側</h1>
    <p>msg: {{ msg }}</p>

    <iframe
      src="http://localhost:3000"
      width="300"
      height="300"
    />
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      msg: '',
    };
  },
  methods: {
    receive(e) {
      if (e.origin !== 'http://localhost:3000') return;
      this.msg = e.data;
    },
  },
  mounted() {
    this.$nextTick(() => {
      window.addEventListener('message', this.receive, false);
    });
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

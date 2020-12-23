<template>
  <div class="result">
    <p>Reaction Time : {{ timeResult }}</p>
    <span>Thanks for playing you have a {{ reflex }}</span>
  </div>
</template>

<script>
export default {
  props: ['timeResult'],
  data() {
    return {
      reflex: this.checkReflex(),
    }
  },
  methods: {
    checkReflex() {
      if ( this.timeResult <= 250 ) {
        return 'NINJA REFLEX :o';
      } else if ( this.timeResult < 350 ) {
        return 'RAPID REFLEX :u';
      } else if ( this.timeResult < 500 ) {
        return 'CAT REFLEX :)';
      } else if ( this.timeResult < 600) {
        return 'TURTLE POWER REFLEX :|';
      } else {
        return 'SNAIL REFLEX :('
      }
    }
  }
}
</script>

<style scoped>
  .result {
    color: darkgreen;
    font-size: x-large;
  }
</style>
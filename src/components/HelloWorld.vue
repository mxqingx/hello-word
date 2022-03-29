<template>
  <div class="hello">
    <m-form></m-form>
  </div>
</template>

<script>
import form from '@/components/form'
export default {
  name: 'HelloWorld',
  components: {
    'm-form': form
  },
  props: {
    msg: String
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

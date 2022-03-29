<template>
  <div class=''>
    <slot name="default"></slot>
  </div>
</template>

<script>

export default {
  name: 'k-form',
  provide () {
    return {
      form: this //传递form实例给后代
    }
  },
  props: {
    model: {
      type: Object,
      required: true
    },
    rules: {
      type: Object
    }
  },
  components: {},
  data() {
    return {

    }
  },
  computed: {},
  watch: {},
  methods: {
    validate (cb) {
      const tasks = this.$children.map(item => item.validate())
      Promise.all(tasks).then(() => {
        cb(true)
      }).catch(() => {
        cb(false)
      })
    }
  },
  created() {

  },
  mounted() {

  },
}
</script>
<style scoped lang='scss'>

</style>
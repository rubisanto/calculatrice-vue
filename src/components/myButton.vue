<template>
    <div>
      <button @click="$emit('operation', text)">{{ text }}</button>
    </div>
</template>
  
<script>
  export default {
    props: {
      text: {
        type: String,
        required: true
      }
    },
    methods: {
    
    }
  }
</script>

<style scoped>
</style>
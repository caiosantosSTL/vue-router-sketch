<template>
  <h3>{{ text || 'Default value'}}</h3>
</template>

<script>
export default {
    props:{
        text: String
    }
}
</script>

<style>

</style>
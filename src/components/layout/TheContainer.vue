<template>
    <div class="a-container">
        <TheHeader/>
        <TheContent/>
    </div>
</template>

<script>
import TheHeader from './TheHeader.vue'
import TheContent from './TheContent.vue'

export default {
    components: {
    // HelloWorld
    TheHeader,
    TheContent,

  }
}
</script>

<style scoped>
.a-container {
    flex: 1;
}
</style>
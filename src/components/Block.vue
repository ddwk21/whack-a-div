<template>
  <div class="block">
    Click Me!
  </div>
</template>

<script>
export default {
    props:['delay'],

    mounted() {
      console.log('Component Mounted')
    }
    
}
</script>

<style>
    .block {
        width: 400px;
        border-radius: 20px;
        background: rgb(63, 120, 120);
        color: white;
        text-align: center;
        padding: 100px 0;
        margin: 40px auto;
    }

</style>
<template>
  <footer>
        &copy; Scott Gruber {{currentYear}}<br>
        <span class="about" @click="$emit('aboutOpen')">About</span>
  </footer>
</template>

<script>
export default {
    name: 'Footer',
    data(){
        return {
            currentYear: new Date().getFullYear()
        }
    }
}
</script>

<style scoped>
    footer{
        padding: 40px 0px;
        text-align: center;
        font-size: 1rem;
        line-height: 2rem;
    }

    .about{
        cursor: pointer;
        color: steelblue;
    }
</style>
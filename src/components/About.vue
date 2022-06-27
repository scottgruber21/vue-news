<template>
  <div class="about-wrapper" @click.self="$emit('aboutClose')">
    <div class="about-content">
        <h2>About News Today</h2>
        <p>News Today was created using Vue and the Vue router, as well as CSS Grid elements.<br><br>News data comes from the <a href="https://newsapi.org/" target="_blank">News API</a></p>
        <button @click="$emit('aboutClose')">Close</button>
    </div>
  </div>
</template>

<script>
export default {
    name: 'About'
}
</script>

<style scoped>
    button{
        background: steelblue;
        color: white;
        padding: 10px;
        border: none;
        border-radius: 3px;
        font-size: 18px;
        cursor: pointer;
    }

    .about-wrapper{
        background-color: rgba(0, 0, 0, 0.7);
        position: fixed;
        top: 0px;
        left: 0px;
        width: 100%;
        height: 100vh;
        z-index: 999;
    }

    .about-content{
        background-color: white;
        color: black;
        margin: 120px auto 0px auto;
        max-width: 800px;
        padding: 30px;
    }
    .about-content p{
        font-size: 1.1rem;
    }
</style>
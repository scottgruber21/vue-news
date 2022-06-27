<template>
<div class="select-articles">
<label for="numArticles">Articles: </label>
    <select name="numArticles" id="numArticles" @change="handleChange">
        <option value="10">10</option>
        <option value="20">20</option>
        <option value="30">30</option>
    </select>
    </div>
</template>

<script>
export default{
    name: 'NumArticles',
    data(){
        return {
            numArticles: 10
        }
    },
    methods: {
        handleChange(event){
            this.numArticles = event.target.value
            this.$emit('numChange', this.numArticles)
        }
    }
}
</script>

<style scoped>
    .select-articles{
        text-align: right;
    }

    label, select, option{
        font-size: 1.2rem;
    }
</style>
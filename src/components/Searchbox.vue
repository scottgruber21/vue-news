<template>
<div class="form-control">
    <form @submit="handleSubmit">
    <input type="text" id="search" name="search" v-model="search">
    <button>Search</button>
    </form>
</div>
</template>

<script>
export default{
    name: 'Searchbox',
    data(){
        return{
            search: ''
        }
    },
    methods:{
        handleSubmit(e){
            e.preventDefault()
            this.$emit('submitted', this.search)
            this.$router.push('/search/' + this.search)
        }
    }
}
</script>

<style scoped>
    .form-control{
        padding: 20px 0px;
    }

    input{
        margin-right: 20px;
        padding: 10px;
        border-radius: 5px;
        font-size: 18px;
    }

    input:focus{
        outline: none;
        border: 2px solid steelblue;
    }

    button{
        background: steelblue;
        color: white;
        padding: 10px;
        border: none;
        border-radius: 3px;
        font-size: 18px;
    }

</style>
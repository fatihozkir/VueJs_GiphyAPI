<template>
    <div class="search">
        <input type="text" v-model="query" @keypress.enter="handleSearch">
        <button @click="handleSearch">Search</button>
    </div>
</template>

<script>
export default {
   data: function () {
        return {
            query: ''
        }
    },
    methods:
    {
        handleSearch(){
            this.$emit('SearchRequested',this.query);
        }
    }
}
</script>
<style>
    .search input{
        padding: 10px 20px;
        border: 1px solid #ccc;
        border-radius: 5px;
        width: 400px;
    }
    .search button{
        padding:5px 15px;
        border:1px solid #ccc;
        background-color: #4183c4;
        font-size: 15px;
        border-radius: 4px;
        color:#fff;
    }
</style>

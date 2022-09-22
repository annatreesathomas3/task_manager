<template>
    <footer>
        <p>
            Copyright &copy; 2021
        </p>
        <router-link to="/about" class="about">About</router-link>
    </footer>
</template>
<script>
export default {
   name:'Footer' 
}
</script>
<style scoped>
.about{
    cursor: pointer;
    text-decoration: none;
}
</style>
<template>
    <div class="about page">
        <h1>Hello there</h1>
        <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Iure, ullam vero! Sapiente magni provident, nobis assumenda quis quod magnam voluptate repudiandae sunt mollitia eos velit, maxime, praesentium voluptatem officiis nam.</p>
    </div>
</template>

<script>
export default {
    name:'About',
    data(){
        return {
            their_name:this.$route.params.name
        };
    }
}
</script>

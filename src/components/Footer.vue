<script setup lang="ts">
    import {ref} from 'vue';
    
</script>

<template>
    <div class="gif">
        <img src="https://i.pinimg.com/originals/d5/a5/22/d5a5220aa315b5d832630c519ca3d4a2.gif" alt="" class="gifs">
    </div>
</template>


<style scoped>
.gif{
    width: 100%;
    margin: 0;
    padding: 0;
    background-color: rgb(255, 255, 255);
    display: flex;
    justify-content: center;
    align-items: center;
}

.gifs{
    width: 100%;
    height: 350px;
    object-fit: cover;
    margin: 0;
    display: block;
}
</style>
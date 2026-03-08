<script setup lang="ts">
    import {ref} from 'vue';
    
</script>

<template>
    <div class="footer-container">
        <div class="illustration-area">
            <div class="grid-pattern"></div>
            <div class="gif">
                <img src="https://i.pinimg.com/originals/bb/4e/1f/bb4e1fe13db51fe97c6dd2c33f954d15.gif" alt="" class="gifs">
            </div>
        </div>
    </div>
</template>

<style scoped>
.footer-container {
    width: 100%;
    background-color: white;
}

.illustration-area {
    position: relative;
    width: 100%;
    height: 300px;
    background-color: #A3FF00; /* Neon Green */
    display: flex;
    justify-content: center;
    align-items: center;
    overflow: hidden;
}

.grid-pattern {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-image: 
        linear-gradient(rgba(0, 0, 0, 0.05) 1px, transparent 1px),
        linear-gradient(90deg, rgba(0, 0, 0, 0.05) 1px, transparent 1px);
    background-size: 30px 30px;
    pointer-events: none;
}

.gif {
    position: relative;
    z-index: 2;
    display: flex;
    justify-content: center;
    align-items: center;
}

.gifs {
    max-width: 150px;
    height: auto;
}

@media (max-width: 768px) {
    .illustration-area {
        height: 200px;
    }
    .gifs {
        max-width: 100px;
    }
}
</style>
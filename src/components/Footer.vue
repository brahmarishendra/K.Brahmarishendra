<script setup lang="ts">
    import {ref} from 'vue';
    
</script>

<template>
    <div class="footer-container">
        <div class="gif">
            <img src="https://i.pinimg.com/originals/bb/4e/1f/bb4e1fe13db51fe97c6dd2c33f954d15.gif" alt="" class="gifs">
        </div>
        <div class="illustration-area">
            <div class="grid-pattern"></div>
            <svg viewBox="0 0 24 24" fill="none" xmlns="http://www.w3.org/2000/svg" class="arrow">
                <path d="M5 12H19M19 12L12 5M19 12L12 19" stroke="#121212" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
            </svg>
        </div>
    </div>
</template>


<style scoped>
.footer-container {
    width: 100%;
    background-color: #fff;
}

.gif{
    width: 100%;
    min-height: 100px;
    padding: 2rem 0;
    background-color: rgb(255, 255, 255);
    display: flex;
    justify-content: center;
    align-items: center;
}

.gifs{
    width: 100%;
    height: auto;
    max-width: 600px;
}

.illustration-area {
    display: none;
    height: 300px;
    background-color: #38ef7d; /* Vibrant Green */
    position: relative;
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
}

.arrow {
    width: 50%;
    height: 50%;
    position: relative;
    z-index: 2;
    transform: rotate(-45deg); /* Pointing up-right */
}

@media screen and (max-width: 1200px) {
    .illustration-area {
        display: flex;
    }
}

@media screen and (max-width: 768px) {
    .illustration-area {
        height: 200px;
    }
}
</style>
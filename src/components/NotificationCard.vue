<script setup lang="ts">
defineProps<{
    type: 'EMAIL' | 'MESSAGE' | 'BOOKED';
    title: string;
    subtitle: string;
    stats: string;
    time: string;
}>();
</script>

<template>
    <div class="notification-card" :class="type.toLowerCase()">
        <div class="card-header">
            <div class="icon-title">
                <div class="icon">
                    <i v-if="type === 'EMAIL'" class="fa-solid fa-envelope"></i>
                    <i v-else-if="type === 'MESSAGE'" class="fa-solid fa-comment"></i>
                    <i v-else-if="type === 'BOOKED'" class="fa-solid fa-calendar-check"></i>
                </div>
                <span class="type-text">{{ type === 'BOOKED' ? 'MEETING BOOKED' : 'NEW ' + type }}</span>
            </div>
            <span class="time-text">{{ time }}</span>
        </div>
        <div class="card-content">
            <h4 class="title">{{ title }}</h4>
            <p class="subtitle">{{ subtitle }}</p>
        </div>
        <div class="card-footer">
            <span class="stats">{{ stats }}</span>
        </div>
    </div>
</template>

<style scoped>
.notification-card {
    background: #fff9e6; /* Light yellow tint */
    border: 1px solid #121212;
    border-radius: 12px;
    padding: 1rem;
    width: 280px;
    box-shadow: 6px 6px 0px #121212;
    position: absolute;
    z-index: 10;
}

.card-header {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.8rem;
}

.icon-title {
    display: flex;
    align-items: center;
    gap: 8px;
}

.icon {
    font-size: 0.9rem;
}

.type-text {
    font-size: 0.7rem;
    font-weight: 700;
    letter-spacing: 0.5px;
}

.time-text {
    font-size: 0.7rem;
    color: #4b5563;
}

.card-content .title {
    font-size: 0.85rem;
    font-weight: 800;
    margin-bottom: 2px;
}

.card-content .subtitle {
    font-size: 0.75rem;
    color: #4b5563;
    margin-bottom: 8px;
}

.card-footer .stats {
    font-size: 0.7rem;
    font-weight: 600;
    color: #4b5563;
}
</style>

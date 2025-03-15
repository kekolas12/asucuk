<!-- src/components/LoginScreen.vue -->
<template>
    <div class="flex flex-col items-center justify-center min-h-screen p-4">
        <div class="text-xs md:text-sm overflow-hidden w-full max-w-2xl mb-8 typing-effect">
            {{ displayedBinary }}
        </div>

        <div class="glitch-container mb-8">
            <h1 class="text-2xl md:text-4xl glitch-text" data-text="ISMINIZI GIRIN">ISMINIZI GIRIN</h1>
        </div>

        <div class="w-full max-w-md">
            <input type="text" v-model="name" @keyup.enter="checkName"
                class="w-full bg-black border-2 border-green-500 p-3 text-green-500 focus:outline-none focus:border-green-400"
                placeholder="_" />

            <div v-if="showError" class="mt-4 text-red-500">
                Access Denied. Try Again.
            </div>

            <div v-if="showSuccess" class="mt-4 text-green-400">
                Giriş onaylandı...
            </div>
        </div>
    </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const emit = defineEmits(['login-success']);
const name = ref('');
const showError = ref(false);
const showSuccess = ref(false);
const displayedBinary = ref('');
let binaryInterval;

const generateBinary = () => {
    return Array(100).fill(0).map(() => Math.random() > 0.5 ? '1' : '0').join(' ');
};

const updateBinary = () => {
    displayedBinary.value = generateBinary();
};

const checkName = () => {
    if (name.value.toLowerCase() === 'asu') {
        showError.value = false;
        showSuccess.value = true;
        setTimeout(() => {
            emit('login-success');
        }, 1500);
    } else {
        showError.value = true;
        showSuccess.value = false;
    }
};

onMounted(() => {
    binaryInterval = setInterval(updateBinary, 100);
});

onUnmounted(() => {
    clearInterval(binaryInterval);
});
</script>

<style scoped>
.glitch-text {
    position: relative;
    animation: glitch 1s linear infinite;
}

.glitch-text::before,
.glitch-text::after {
    content: attr(data-text);
    position: absolute;
    left: 0;
}

.glitch-text::before {
    animation: glitch-top 1s linear infinite;
    clip-path: polygon(0 0, 100% 0, 100% 33%, 0 33%);
    -webkit-clip-path: polygon(0 0, 100% 0, 100% 33%, 0 33%);
}

.glitch-text::after {
    animation: glitch-bottom 1.5s linear infinite;
    clip-path: polygon(0 67%, 100% 67%, 100% 100%, 0 100%);
    -webkit-clip-path: polygon(0 67%, 100% 67%, 100% 100%, 0 100%);
}

@keyframes glitch {

    2%,
    64% {
        transform: translate(2px, 0) skew(0deg);
    }

    4%,
    60% {
        transform: translate(-2px, 0) skew(0deg);
    }

    62% {
        transform: translate(0, 0) skew(5deg);
    }
}

@keyframes glitch-top {

    2%,
    64% {
        transform: translate(2px, -2px);
    }

    4%,
    60% {
        transform: translate(-2px, 2px);
    }

    62% {
        transform: translate(13px, -1px) skew(-13deg);
    }
}

@keyframes glitch-bottom {

    2%,
    64% {
        transform: translate(-2px, 0);
    }

    4%,
    60% {
        transform: translate(-2px, 0);
    }

    62% {
        transform: translate(-22px, 5px) skew(21deg);
    }
}
</style>
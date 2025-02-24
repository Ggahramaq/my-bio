<script setup>
import { ref } from 'vue';

const nickname = ref('ggahramaq');
const isnoname = ref(true);
const title = ref('');

const addCharacter = () => {
    title.value += nickname.value[title.value.length]
}

const removeCharacter = () => {
    title.value = title.value.slice(0, title.value.length-1)
}

const add = () => {
    if (isnoname.value) {
        if (title.value.length < nickname.value.length) {
            addCharacter();
        } else {
            isnoname.value = false;
            removeCharacter();
        }
    } else {
        if (title.value.length > 0) {
            removeCharacter();
        } else {
            isnoname.value = true;
            // addCharacter();
        }
    }
    document.title = title.value.length > 0 ? title.value : 'My Bio'
};
setInterval(add, 200);
</script>

<template>
    <div class="background h-screen w-screen bg-[#16191f] flex justify-center">
        <div class="w-[555.4px] h-[464.4px] border-[0.8px] border-[#151f27] bg-[#2a2b2b] mt-16 rounded-[12px]"></div>
    </div>
</template>
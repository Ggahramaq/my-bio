<script setup>
import { ref } from 'vue';
import avatar from '@/assets/img/avatar.png';
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
        if (title.value.length > 1) {
            removeCharacter();
        } else {
            isnoname.value = true;
            // addCharacter();
        }
    }
    document.title = title.value
};
setInterval(add, 300);
</script>

<template>
    <div class="background h-screen w-screen bg-[#16191f] flex justify-center">
        <div class="w-[557px] h-[466px] border-[0.8px] border-[#151f27] bg-[#2a2b2b] mt-16 rounded-[12px]">
            <div class="w-[555.4px] h-[464.4px] p-[32.5px] items-center flex flex-col">
                <img :src="avatar" class="h-[91px] w-[91px] aspect-square border rounded-full">
                <div class="nickname text-[20px] text-[#757575] mt-6">Ggahramaq</div>
            </div>
        </div>
    </div>
</template>
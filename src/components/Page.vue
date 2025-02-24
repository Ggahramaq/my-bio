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
        <div class="w-[557px] h-[466px] absolute border-[0.8px] border-[#1b2731] bg-[#2a2b2b] mt-16 rounded-[12px]">
            <div class="w-[555.4px] h-[464.4px] p-[32.5px] items-center flex flex-col">
                <img :src="avatar" class="h-[91px] w-[91px] aspect-square border rounded-full">
                <div class="nickname text-[20px] text-[#757575] mt-6">Ggahramaq</div>
                <div class="flex">
                <!-- Icons -->
                </div>

                <!-- <div class="roles flex flex-wrap gap-2 justify-center mt-7"> -->
                <div class="nickname flex flex-wrap gap-2 justify-center mt-3">
                    <div class="h-[24.35px] w-[88.77px] px-[9.75px] py-[3.25px] border-[0.8px] border-[#ffffff] text-white rounded-full flex justify-center items-center">WEB</div>
                    <div class="h-[24.35px] w-[88.77px] px-[9.75px] py-[3.25px] border-[0.8px] border-[#ffffff] text-white rounded-full flex justify-center items-center">IT</div>
                </div>
                <div class="nickname mt-5 text-[#9b9592]">
                Hi there!
                </div>
                <div class="nickname text-[#9b9592]">
                    I am trying to become a Web-developer.
                </div>
                <br>
                <hr class="w-[490.4px] h-[0.8px]">
                <br>
                <div class="profile text-[#5982ac]">Welcome to my profile.</div>
                <br>
                <div class="flex text-white">
                    <div class="pi pi-flag text-red-500 mt-[4px]"></div>
                    <div class="ml-[5px]">
                        <!-- <div class="nickname text-blue-400">Aze</div>
                        <div class="nickname text-red-500">rbay</div>
                        <div class="nickname text-green-400">jan</div> -->
                        Azerbaijan
                    </div>
                </div>
                
            </div>
        </div>
        
    </div>
</template>
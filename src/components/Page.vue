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
        }
    }
    document.title = title.value
};
setInterval(add, 300);
</script>

<template>
    <div class="background h-screen w-screen bg-[#16191f] flex flex-col items-center justify-center">
        <div class="w-[557px] h-[440px] border-[0.8px] border-[#1b2731] bg-[#2a2b2b] mt-16 rounded-[12px]">
            <div class="w-[555.4px] h-[450.4px] p-[32.5px] items-center flex flex-col">
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
                    <!-- <div class="pi pi-flag text-red-500 mt-[4px]"></div> -->
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 32 32"><path fill="#dd4446" d="M1 11H31V21H1z"></path><path d="M5,4H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z" fill="#52b4de"></path><path d="M5,20H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z" transform="rotate(180 16 24)" fill="#649e3f"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M15.593,19.056c-1.688,0-3.056-1.368-3.056-3.056s1.368-3.056,3.056-3.056c.822,0,1.568,.325,2.117,.853-.669-.889-1.733-1.465-2.932-1.465-2.025,0-3.667,1.642-3.667,3.667s1.642,3.667,3.667,3.667c1.199,0,2.263-.575,2.932-1.465-.549,.528-1.295,.853-2.117,.853Z" fill="#fff"></path><path d="M18.852,13.963l.39,1.096,1.051-.499-.499,1.051,1.096,.39-1.096,.39,.499,1.051-1.051-.499-.39,1.096-.39-1.096-1.051,.499,.499-1.051-1.096-.39,1.096-.39-.499-1.051,1.051,.499,.39-1.096Z" fill="#fff"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>
                    <div class="ml-[5px]">
                        <!-- <div class="nickname text-blue-400">Aze</div>
                        <div class="nickname text-red-500">rbay</div>
                        <div class="nickname text-green-400">jan</div> -->
                        Azerbaijan
                    </div>
                </div>        
            </div>
        </div>
        <div class="flex justify-between gap-4 mt-6">
            <div class="w-[271px] h-[67px] p-3 border-[0.8px] border-[#1b2731] rounded-lg bg-[#2a2b2b]"></div>
            <div class="w-[271px] h-[67px] p-3 border-[0.8px] border-[#1b2731] rounded-lg bg-[#2a2b2b]"></div>
        </div>
    </div>
</template>
<script setup>
import { onMounted, onUnmounted, ref } from 'vue';
import musicavatar from '@/assets/img/musicavatar.jpeg'
import music from '@/assets/music.mp3'
import avatar from '@/assets/img/avatar.png';
const nickname = ref('ggahramaq');
const isnoname = ref(true);
const title = ref('');
const username = ref('ggahramaq');
const audio = ref(new Audio(music));
const toggleMusic = ref(false); 
const toggleScreen = ref(false)
const barwidth = ref(0)
const videoRef = ref(null);
const copyNickname = () => {
    navigator.clipboard.writeText("ggahramaq");
    username.value = "Copied!"
    setTimeout(() => {
        username.value = "ggahramaq";
    }, 1000);
}

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

const currentTime = ref("00:00");
const duration = ref(0);

const updateTime = () => {
  const currentSec = Math.floor(audio.value.currentTime);
  const minutes = Math.floor(currentSec / 60);
  const seconds = currentSec % 60;
  barwidth.value = 259/100*Math.floor(audio.value.currentTime)
  currentTime.value = `${minutes < 10 ? '0' : ''}${minutes}:${seconds < 10 ? '0' : ''}${seconds}`;
};

// 0${audio.value.currentTime%60}:${audio.value.currentTime-(audio.value.currentTime%60)}

onMounted(() => {
  audio.value.addEventListener('timeupdate', updateTime);
  duration.value = audio.value.duration;
});

onUnmounted(() => {
  audio.value.removeEventListener('timeupdate', updateTime);
});


// const musicdata = () => {
//     duration.value = audio.value.duration;
//     currentTime.value = audio.value.currentTime;

//     musicinfo.value[0] = duration.value
//     musicinfo.value[1] = currentTime.value
//     return musicinfo.value
// }
</script>

<template>
    <div class="video absolute">
        <video v-if="toggleScreen" autoplay muted loop ref="videoRef" src="@/assets/video.mp4"></video>
        <video v-else muted loop ref="videoRef" src="@/assets/video.mp4"></video>
    </div>
    <div v-if="toggleScreen" class="background absolute h-186 w-screen flex flex-col items-center">
        <div class="w-[557px] h-[440px] border-[0.8px] border-[#1b2731] bg-[rgba(20, 20, 22, 0.376)] backdrop-blur-[40px] mt-16 rounded-[12px]">
            <div class="w-[555.4px] h-[450.4px] p-[32.5px] items-center flex flex-col">
                <img :src="avatar" class="h-[91px] w-[91px] aspect-square border rounded-full">
                <div class="nickname text-[20px] text-[#757575] mt-5">Ggahramaq</div>
                <div class="flex">
                <!-- Icons -->
                </div>

                <!-- <div class="roles flex flex-wrap gap-2 justify-center mt-7"> -->
                <div class="nickname flex flex-wrap gap-2 justify-center mt-3">
                    <div class="h-[24.35px] w-[88.77px] px-[9.75px] py-[3.25px] border-[1px] border-[#1B2A37] text-white rounded-full d flex justify-center items-center">WEB</div>
                    <div class="h-[24.35px] w-[88.77px] px-[9.75px] py-[3.25px] border-[1px] border-[#1B2A37] text-white rounded-full d flex justify-center items-center">IT</div>
                </div>
                <div class="m mt-5 text-[#a8a29e]">
                Hi there!
                </div>
                <div class="m text-[#a8a29e]">
                    I am trying to become a Web-developer.
                </div>
                <br>
                <div class="w-[490.4px] h-[0.8px] bg-[#484848]"></div>
                <br>
                <div class="d theme-color">Welcome to my profile.</div>
                <br>
                <div class="flex text-white">
                    <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 32 32"><path fill="#dd4446" d="M1 11H31V21H1z"></path><path d="M5,4H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z" fill="#52b4de"></path><path d="M5,20H27c2.208,0,4,1.792,4,4v4H1v-4c0-2.208,1.792-4,4-4Z" transform="rotate(180 16 24)" fill="#649e3f"></path><path d="M27,4H5c-2.209,0-4,1.791-4,4V24c0,2.209,1.791,4,4,4H27c2.209,0,4-1.791,4-4V8c0-2.209-1.791-4-4-4Zm3,20c0,1.654-1.346,3-3,3H5c-1.654,0-3-1.346-3-3V8c0-1.654,1.346-3,3-3H27c1.654,0,3,1.346,3,3V24Z" opacity=".15"></path><path d="M15.593,19.056c-1.688,0-3.056-1.368-3.056-3.056s1.368-3.056,3.056-3.056c.822,0,1.568,.325,2.117,.853-.669-.889-1.733-1.465-2.932-1.465-2.025,0-3.667,1.642-3.667,3.667s1.642,3.667,3.667,3.667c1.199,0,2.263-.575,2.932-1.465-.549,.528-1.295,.853-2.117,.853Z" fill="#fff"></path><path d="M18.852,13.963l.39,1.096,1.051-.499-.499,1.051,1.096,.39-1.096,.39,.499,1.051-1.051-.499-.39,1.096-.39-1.096-1.051,.499,.499-1.051-1.096-.39,1.096-.39-.499-1.051,1.051,.499,.39-1.096Z" fill="#fff"></path><path d="M27,5H5c-1.657,0-3,1.343-3,3v1c0-1.657,1.343-3,3-3H27c1.657,0,3,1.343,3,3v-1c0-1.657-1.343-3-3-3Z" fill="#fff" opacity=".2"></path></svg>
                    <div class="ml-[5px]">
                        Azerbaijan
                    </div>
                </div>        
            </div>
        </div>
        <div class="flex justify-between gap-4 mt-6">
            <div class="w-[271px] h-[67px] p-3 border-[0.8px] flex items-center border-[#1b2731] rounded-lg bg-[rgba(20, 20, 22, 0.376)] backdrop-blur-[40px]">
                <div class="h-[45.5px] w-[45.5px] border-[0.8px] flex justify-center items-center bg-[rgba(255, 255, 255, 0.03)] rounded-lg">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24" class="fill-[#75bfff]"><path d="M20.317 4.3698a19.7913 19.7913 0 00-4.8851-1.5152.0741.0741 0 00-.0785.0371c-.211.3753-.4447.8648-.6083 1.2495-1.8447-.2762-3.68-.2762-5.4868 0-.1636-.3933-.4058-.8742-.6177-1.2495a.077.077 0 00-.0785-.037 19.7363 19.7363 0 00-4.8852 1.515.0699.0699 0 00-.0321.0277C.5334 9.0458-.319 13.5799.0992 18.0578a.0824.0824 0 00.0312.0561c2.0528 1.5076 4.0413 2.4228 5.9929 3.0294a.0777.0777 0 00.0842-.0276c.4616-.6304.8731-1.2952 1.226-1.9942a.076.076 0 00-.0416-.1057c-.6528-.2476-1.2743-.5495-1.8722-.8923a.077.077 0 01-.0076-.1277c.1258-.0943.2517-.1923.3718-.2914a.0743.0743 0 01.0776-.0105c3.9278 1.7933 8.18 1.7933 12.0614 0a.0739.0739 0 01.0785.0095c.1202.099.246.1981.3728.2924a.077.077 0 01-.0066.1276 12.2986 12.2986 0 01-1.873.8914.0766.0766 0 00-.0407.1067c.3604.698.7719 1.3628 1.225 1.9932a.076.076 0 00.0842.0286c1.961-.6067 3.9495-1.5219 6.0023-3.0294a.077.077 0 00.0313-.0552c.5004-5.177-.8382-9.6739-3.5485-13.6604a.061.061 0 00-.0312-.0286zM8.02 15.3312c-1.1825 0-2.1569-1.0857-2.1569-2.419 0-1.3332.9555-2.4189 2.157-2.4189 1.2108 0 2.1757 1.0952 2.1568 2.419 0 1.3332-.9555 2.4189-2.1569 2.4189zm7.9748 0c-1.1825 0-2.1569-1.0857-2.1569-2.419 0-1.3332.9554-2.4189 2.1569-2.4189 1.2108 0 2.1757 1.0952 2.1568 2.419 0 1.3332-.946 2.4189-2.1568 2.4189Z"></path></svg>
                </div>
                <div class="profile ml-2 text-white text-[17px]" id="nickname">{{username}}</div>
                <div class="ml-auto cursor-pointer" @click="copyNickname"> 
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="20" height="20" class="fill-[#75bfff] hover:fill-[#294ea4] transition delay-200 ease-out"><path d="m6 19v2c0 .621.52 1 1 1h2v-1.5h-1.5v-1.5zm7.5 3h-3.5v-1.5h3.5zm4.5 0h-3.5v-1.5h3.5zm4-3h-1.5v1.5h-1.5v1.5h2c.478 0 1-.379 1-1zm-1.5-1v-3.363h1.5v3.363zm0-4.363v-3.637h1.5v3.637zm-13-3.637v3.637h-1.5v-3.637zm11.5-4v1.5h1.5v1.5h1.5v-2c0-.478-.379-1-1-1zm-10 0h-2c-.62 0-1 .519-1 1v2h1.5v-1.5h1.5zm4.5 1.5h-3.5v-1.5h3.5zm3-1.5v-2.5h-13v13h2.5v-1.863h1.5v3.363h-4.5c-.48 0-1-.379-1-1v-14c0-.481.38-1 1-1h14c.621 0 1 .522 1 1v4.5h-3.5v-1.5z"></path></svg>
                </div>
            </div>
            <div class="w-[271px] h-[67px] p-3 border-[0.8px] flex items-center border-[#1b2731] rounded-lg bg-[rgba(20, 20, 22, 0.376)] backdrop-blur-[40px]">
                <div class="h-[45.5px] w-[45.5px] border-[0.8px] flex justify-center items-center bg-[rgba(255, 255, 255, 0.03)] rounded-lg">
                    <svg xmlns="http://www.w3.org/2000/svg" width="33" height="33" viewBox="0 0 30 30" class="fill-[#75bfff]"> <path d="M15,3C8.373,3,3,8.373,3,15c0,5.623,3.872,10.328,9.092,11.63C12.036,26.468,12,26.28,12,26.047v-2.051 c-0.487,0-1.303,0-1.508,0c-0.821,0-1.551-0.353-1.905-1.009c-0.393-0.729-0.461-1.844-1.435-2.526 c-0.289-0.227-0.069-0.486,0.264-0.451c0.615,0.174,1.125,0.596,1.605,1.222c0.478,0.627,0.703,0.769,1.596,0.769 c0.433,0,1.081-0.025,1.691-0.121c0.328-0.833,0.895-1.6,1.588-1.962c-3.996-0.411-5.903-2.399-5.903-5.098 c0-1.162,0.495-2.286,1.336-3.233C9.053,10.647,8.706,8.73,9.435,8c1.798,0,2.885,1.166,3.146,1.481C13.477,9.174,14.461,9,15.495,9 c1.036,0,2.024,0.174,2.922,0.483C18.675,9.17,19.763,8,21.565,8c0.732,0.731,0.381,2.656,0.102,3.594 c0.836,0.945,1.328,2.066,1.328,3.226c0,2.697-1.904,4.684-5.894,5.097C18.199,20.49,19,22.1,19,23.313v2.734 c0,0.104-0.023,0.179-0.035,0.268C23.641,24.676,27,20.236,27,15C27,8.373,21.627,3,15,3z"></path></svg>
                </div>
                <div class="profile ml-2 text-white text-[17px]">Ggahramaq</div>
                <div class="ml-auto cursor-pointer">
                    <a href="https://github.com/Ggahramaq">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="20" height="20" class="fill-[#75bfff] hover:fill-[#294ea4] transition delay-200 ease-out"><path d="M16.6 17a1 1 0 0 1-.6-1v-2.5H3a1 1 0 0 1-1-1v-1q0-1 1-1h13V8a1 1 0 0 1 1.7-.7l4 4q.6.7 0 1.4l-4 4a1 1 0 0 1-1 .2"></path></svg>
                    </a>
                </div>
            </div>
        </div>
        <div class="flex mt-6">
            <div class="w-[557px] h-[86px] p-3 border-[0.8px] flex border-[#1b2731] rounded-lg bg-[rgba(20, 20, 22, 0.376)] backdrop-blur-[40px] relative">
                <div class="h-[65px] w-[65px] border-[0.8px] flex justify-center items-center rounded-lg bg-[#1f252b]">
                    <img :src="musicavatar">
                </div>
                <div class="ml-2 text-white flex flex-col">
                    <span class="text-[17px]">kitty phonk</span>
                    <div class="flex mt-1">
                        <span class="text-[14px] text-gray-400">{{currentTime}}</span> 
                        <div class="mt-[6.5px] ml-2 w-[232.78px] h-[8.13px] bg-amber-50 border rounded-full"></div>
                        <div class="mt-[6.5px] ml-[41.1px] absolute h-[8.13px] bg-amber-800 border rounded-full" :style="`width: ${barwidth}px;`"></div>
                        <span class="ml-2 mt-[-0.5px] text-[14px] text-gray-400">01:30</span> 
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" width="24" height="24" @click="showmusic" class="cursor-pointer size-5 ml-2"><path d="M21.4 9.4a3 3 0 0 1 0 5.2l-12.8 7C6.6 22.7 4 21.3 4 19V5c0-2.3 2.5-3.7 4.6-2.6z"></path></svg>
                        <div class="mt-[5.5px] ml-3 w-[65px] h-[8.13px] bg-amber-50 border rounded-full"></div>
                    </div>
                    
                </div>
                <!--
                <audio controls>
  <source src="@/assets/music.mp3" type="audio/mpeg">
Your browser does not support the audio element.
</audio>-->
            </div>
        </div> 

    </div>
    <div v-else class="absolute">
        <div class="h-186 w-screen bg-none backdrop-blur-[30px] text-2xl b text-red-500 flex justify-center items-center">
            <div class="cursor-pointer" @click="toggleScreen = !toggleScreen">
                CLICK PLEASE</div>
            </div>
    </div>
</template>

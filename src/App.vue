<script setup>
import { ref } from 'vue';
import ecualizer from "./components/ecualizador.vue";
import pletina from "./components/pletina.vue";


import track01 from '@/assets/music/Beat It - Michael Jackson (Lyrics).ogg'
import track02 from '@/assets/music/Michael Jackson - Bad (lyrics).ogg'
import track03 from '@/assets/music/Michael Jackson - Rock With You (Official Video - Upscaled).m4a'
import track04 from '@/assets/music/Michael Jackson - You Rock My World (lyrics).ogg'
import track05 from '@/assets/music/Michael Jackson – Remember the Time (Lyrics).ogg'

const trackList= [
    track01,
    track02,
    track03,
    track04,
    track05
]

const tracksTotal = trackList.length -1
let trackActual = 0

const player = ref (null)
const wheelLeft = ref (null)
const wheelRight = ref (null)
const rotate = ref (null)

function playContent(){
    player.value.play()
    rotate.value = true
}

function pauseContent(){
    player.value.pause()
    rotate.value = false
}

function stopContent(){
    player.value.pause()
    player.value.currentTime = 0
    rotate.value = false

}


function trackNext(){
    if (trackActual < tracksTotal){
        trackActual++
        player.value.src = trackList [trackActual]
        player.value.play()
        rotate.value = true
    }
}


function trackPrevious(){
    if (trackActual > 0){
        trackActual--
        player.value.src = trackList [trackActual]
        player.value.play()
        rotate.value = true
    }
}


</script>

<template>


<ecualizer />

    <div ref="pletina">
        <div ref="cassette" id="cassette">
            <img :src="ViniloMj" class ="cassete-img">
            <img ref="wheel-left" :src="CasseteWheel" class="wheel-left" :class="{'cassette-rotate': rotate}">
            <img ref="wheel-right" :src="CasseteWheel" class="wheel-right" :class="{'cassette-rotate': rotate}">
        </div>
    </div>
    <audio ref="player">
        <source :src="trackList[trackActual]" type="audio/ogg">
    </audio>

    <div id="pletina">
        <pletina icon="iconBw" @click-icon="trackPrevious" />
        <pletina icon="iconPlay" @click-icon="playContent" />
        <pletina icon="iconStop" @click-icon="stopContent" />
        <pletina icon="iconPause" @click-icon="pauseContent" />
        <pletina icon="iconFw" @click-icon="trackNext" />
    </div>
</template>

<style>

    body {
        background-color: #beb4aa;
    }

    #app{
        margin: 5% auto;
        width: 30%;
    }

    
  #pletina{
    display: grid;
    grid-template-columns: repeat(5, 1fr);
    justify-content: center;
    justify-items: center;
  }

  #cassette{
    position: relative;
    width: 100%;
  }

  .cassette-img {
    width: 100%;
    border: solid 1px;
    border: solid 1px grey;
    border-radius: 8px;
    box-shadow: 0 0 5px black;
  }

  .wheel-left{
    position: absolute;
    bottom: 43.8%;
    left: 24.2%;
    width: 100%;
    max-width: 12%;
  }

  .wheel-right{
    position: absolute;
    bottom: 43.8%;
    left: 63.4%;
    width: 100%;
    max-width: 12%;
  }

  .cassette-rotate {
    animation: spin 2s linear infinite;
  }

  @keyframes spin {
    from {
      transform: rotate(0deg);
    }
    to {
      transform: rotate(360deg);
    }
  }

  @media (max-width: 600px){
     #app{
      margin:20% auto;
      width: 80%;
    }
  }
</style>

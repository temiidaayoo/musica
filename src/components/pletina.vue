<script setup>
    import iconPlay from '@/assets/icon-play.png'
    import iconBw from '@/assets/icon-bw.png'
    import iconFw from '@/assets/icon-fw.png'
    import iconPause from '@/assets/icon-pause.png'
    import iconStop from '@/assets/icon-stop.png'

    const icons = {
        iconPlay,
        iconBw,
        iconFw,
        iconPause,
        iconStop
    }

const props =defineProps({
    icon: {
        type: String,
        required: true
    }
})


const emit = defineEmits(['clickIcon'])



</script>

<template>

    <div class="buttons">
        <img class="icon-player" :src="icons[icon]" 
        :src="button"
             @click="emit('clickIcon')"
             alt="icon">
             
        >   
    </div>

</template>

<style scoped>
    .buttons{
        text-align: center;
    }
     .pletina-button{
    display: block;
    border: solid1px grey;
    border-radius: 8px;
    box-shadow: 0 0 8px 0 black;
    cursor: pointer;
    width: 90%;


     }

     .pletina-button:hover {
        filter: invert(10%);
     }

     .icon-player{
        margin: 8px 0;
        width: 30%;
        cursor: pointer;
        filter: invert(20%);
     }

     @media (max-width: 600px){
        .buttons{
            width: 90%;
        }
     }

</style>
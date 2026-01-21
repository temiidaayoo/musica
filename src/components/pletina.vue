<script setup>
    import iconPlay from '@/assets/icon-play.png'
    import iconBw from '@/assets/icon-bw.png'
    import iconFw from '@/assets/icon-fw.png'
    import iconPause from '@/assets/icon-pause.png'
    import iconStop from '@/assets/icon-stop.png'
    
    // HE BORRADO EL IMPORT DE button.png PORQUE DABA ERROR

    const icons = {
        iconPlay,
        iconBw,
        iconFw,
        iconPause,
        iconStop
    }

    const props = defineProps({
        icon: {
            type: String,
            required: true
        }
    })

    const emit = defineEmits(['clickIcon'])
</script>

<template>
    <div class="pletina-button" @click="emit('clickIcon')">
        <img class="icon-player" :src="icons[icon]" alt="control icon">
    </div>
</template>

<style scoped>
    /* Estilo del botón creado con CSS (Color gris metálico) */
    .pletina-button {
        display: flex;
        justify-content: center;
        align-items: center;
        
        width: 100%;
        height: 50px; /* Ajusta la altura a tu gusto */
        
        background: linear-gradient(to bottom, #f0f0f0, #d0d0d0); /* Degradado estilo plástico */
        border: 1px solid #999;
        border-radius: 4px;
        box-shadow: 0 2px 4px rgba(0,0,0,0.3);
        cursor: pointer;
        margin: 5px;
    }

    /* Efecto al pulsar el botón */
    .pletina-button:active {
        background: #ccc;
        box-shadow: inset 0 2px 4px rgba(0,0,0,0.3); /* Sombra interior */
        transform: translateY(1px);
    }

    /* El icono dentro del botón */
    .icon-player {
        width: 25px; /* Ajusta el tamaño del icono */
        height: auto;
        opacity: 0.8;
    }

    .pletina-button:hover .icon-player {
        opacity: 1;
    }

    @media (max-width: 600px){
        .pletina-button{
            height: 40px; /* Botones más pequeños en móvil */
        }
    }
</style>
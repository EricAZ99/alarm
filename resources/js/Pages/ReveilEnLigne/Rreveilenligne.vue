<script setup>
import { ref, watch } from "vue"

const props = defineProps({
    heure: Number,
    minute: Number,
    alarmName: String
})

let differenceHours = ref(0)
let differenceMinutes = ref(0)
let differenceSeconds = ref(0)
let alarmSwitch = ref(null)
// let alarmSound = document.getElementById('alarmSound')




function updateTime() {
    clearInterval(alarmSwitch)

    // Obtenir l'heure actuelle
    alarmSwitch = setInterval(() => {
        let alarmSound = document.getElementById('alarmSound');
        let now = new Date();
        let currentHour = now.getHours();
        let currentMinutes = now.getMinutes();
        let currentSeconds = now.getSeconds();

        // Convertir alarmeTime en objet Date

        let alarmeHour = parseInt(props.heure, 10);
        let alarmeMinutes = parseInt(props.minute, 10);
        let alarmeSeconds = parseInt(0, 10);

        // Créer des objets Date pour l'heure actuelle et l'heure d'alarme
        let currentDate = new Date();
        currentDate.setHours(currentHour, currentMinutes, currentSeconds, 0); // Ignorer les millisecondes pour la précision

        let alarmDate = new Date();
        alarmDate.setHours(alarmeHour, alarmeMinutes, alarmeSeconds, 0);

        // Calculer la différence en millisecondes
        let differenceMs = alarmDate.getTime() - currentDate.getTime();

        if (differenceMs < 0) {
            alarmDate.setDate(alarmDate.getDate() + 1); // Ajouter un jour à l'heure d'alarme
            differenceMs = alarmDate.getTime() - currentDate.getTime();
        }
        // Convertir la différence en heures, minutes et secondes
        differenceHours.value = Math.floor(differenceMs / (1000 * 60 * 60));
        differenceMinutes.value = Math.floor((differenceMs % (1000 * 60 * 60)) / (1000 * 60));
        differenceSeconds.value = Math.floor((differenceMs % (1000 * 60)) / 1000);

        
        if (differenceHours.value == 0 && differenceMinutes.value == 0 && differenceSeconds.value == 0) {
            clearInterval(alarmSwitch)
            alarmSound.play()
        }

    }, 1000);
}

updateTime()

// watch(() => props.minute, (oldValue) => {
//   console.log(`Prop 'myProp' a changé de ${oldValue}`);
// });

const startAlarm = () => {

}
</script>

<template>
    <div class="min-w-[20rem] w-[40%] bordser border-red-500 flex flex-col items-center">
        <div id="alarmBorder"
            class="w-[60%] aspect-square rounded-full border-[.6rem] border-red-500 flex flex-col justify-center items-center">
            <h2>{{ alarmName }}</h2>
            <div class="text-[5rem] flex items-center justify-center">
                <span>{{ differenceHours < 10 ? '0' + differenceHours : differenceHours }}</span>
                        <span class="animate-pulse">:</span>
                        <span>{{ differenceMinutes < 10 ? '0' + differenceMinutes : differenceMinutes }}</span>
                                <span class="animate-pulse">:</span>
                                <span>{{ differenceSeconds < 10 ? '0' + differenceSeconds : differenceSeconds }}</span>
            </div>
            <div>
                <span>{{ heure }}</span>
                <span class="animate-pulse">:</span>
                <span>{{ minute }}</span>
            </div>
            <div>
                <!-- <button @click="startAlarm()">Démarrer</button> -->
                <audio id="alarmSound">
                    <source src="../../../../storage/app/public/alame.wav" type="audio/mpeg" preload="auto">
                </audio>
            </div>
        </div>
    </div>
</template>
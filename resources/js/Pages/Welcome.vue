<script setup>
import { onMounted, ref } from "vue";
import Rreveilenligne from "./ReveilEnLigne/Rreveilenligne.vue";
let nowDate = ref(null);
let nowTime = ref(null);
let menu = ref(false);

function getDate() {
    let dateDuJour = new Date()
    let nomsJours = [
        "dimanche", "lundi", "mardi", "mercredi", "jeudi", "vendredi", "samedi"
    ];

    // Récupérer le jour de la semaine, le jour du mois, le mois et l'année
    let jourSemaine = nomsJours[dateDuJour.getDay()]; // Jour de la semaine
    let jour = dateDuJour.getDate(); // Jour du mois (1 à 31)
    let moisIndex = dateDuJour.getMonth(); // Mois (0 à 11)
    let annee = dateDuJour.getFullYear(); // Année sur 4 chiffres

    // Tableau des noms des mois
    let nomsMois = [
        "janvier", "février", "mars", "avril", "mai", "juin",
        "juillet", "août", "septembre", "octobre", "novembre", "décembre"
    ];

    // Récupérer le nom du mois à partir de l'index
    let moisEnLettres = nomsMois[moisIndex];
    nowDate.value = `${jourSemaine} ${jour} ${moisEnLettres} ${annee}`;

}

function updateTime() {
    // Les variables qui permettent d'afficher l'heure actuelle 
    let time = new Date();
    let hrs = time.getHours();
    let mins = time.getMinutes();
    let secs = time.getSeconds();

    // Format minutes and seconds to always have two digits
    hrs = hrs < 10 ? '0' + hrs : hrs;
    mins = mins < 10 ? '0' + mins : mins;
    secs = secs < 10 ? '0' + secs : secs;
    nowTime.value = hrs + ' : ' + mins + ' : ' + secs;
}
onMounted(() => {
    getDate()
    setInterval(updateTime, 1000)
})


function dark_mode() {
    let main_container = document.getElementById("main_container");

    if (main_container.classList.contains("bg-[#f2f7ff]")) {
        main_container.classList.remove("bg-[#f2f7ff]");
        main_container.classList.add("bg-gray-900");
        main_container.classList.add("text-gray-200");
        main_container.style.transition = '1s';
    } else {
        main_container.classList.add("bg-[#f2f7ff]");
        main_container.classList.remove("bg-gray-900");
        main_container.classList.remove("text-gray-200");
    }
}
</script>
<template>
    <div id="main_container"
        class="min-w-[25rem] h-dvh bg-[#f2f7ff] text-[#394e6a] flex flex-col items-center font-medium text-[1.4rem]">
        <nav class="flex justify-between items-center w-full p-4 bordedr border-red-500">
            <div class="flex gap-4">
                <div class=" relative">
                    <span class="cursor-pointer" @click="menu = !menu">
                        <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" class="w-6 h-6">
                            <path d="M3,6H21V8H3V6M3,11H21V13H3V11M3,16H21V18H3V16Z" />
                        </svg>
                    </span>
                    <div v-if="menu"
                        class="absolute border border-red-500 w-[12rem] h-[10rem] flex justify-center text-[1rem] font-normal rounded-2xl">
                        Réveil en ligne
                    </div>
                </div>

                <span>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-6 w-6">
                        <path
                            d="M12,2A7,7 0 0,1 19,9C19,11.38 17.81,13.47 16,14.74V17A1,1 0 0,1 15,18H9A1,1 0 0,1 8,17V14.74C6.19,13.47 5,11.38 5,9A7,7 0 0,1 12,2M9,21V20H15V21A1,1 0 0,1 14,22H10A1,1 0 0,1 9,21M12,4A5,5 0 0,0 7,9C7,11.05 8.23,12.81 10,13.58V16H14V13.58C15.77,12.81 17,11.05 17,9A5,5 0 0,0 12,4Z" />
                    </svg>
                </span>
            </div>
            <div class="text-[2rem] font-bold">Réveil en ligne</div>
            <div class="flex gap-4">
                <span @click="dark_mode">
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-6 w-6">
                        <path
                            d="M7.5,2C5.71,3.15 4.5,5.18 4.5,7.5C4.5,9.82 5.71,11.85 7.53,13C4.46,13 2,10.54 2,7.5A5.5,5.5 0 0,1 7.5,2M19.07,3.5L20.5,4.93L4.93,20.5L3.5,19.07L19.07,3.5M12.89,5.93L11.41,5L9.97,6L10.39,4.3L9,3.24L10.75,3.12L11.33,1.47L12,3.1L13.73,3.13L12.38,4.26L12.89,5.93M9.59,9.54L8.43,8.81L7.31,9.59L7.65,8.27L6.56,7.44L7.92,7.35L8.37,6.06L8.88,7.33L10.24,7.36L9.19,8.23L9.59,9.54M19,13.5A5.5,5.5 0 0,1 13.5,19C12.28,19 11.15,18.6 10.24,17.93L17.93,10.24C18.6,11.15 19,12.28 19,13.5M14.6,20.08L17.37,18.93L17.13,22.28L14.6,20.08M18.93,17.38L20.08,14.61L22.28,17.15L18.93,17.38M20.08,12.42L18.94,9.64L22.28,9.88L20.08,12.42M9.63,18.93L12.4,20.08L9.87,22.27L9.63,18.93Z" />
                    </svg>
                </span>

                <span>
                    <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 24 24" fill="currentColor" class="h-6 w-6">
                        <path
                            d="M12,2A7,7 0 0,1 19,9C19,11.38 17.81,13.47 16,14.74V17A1,1 0 0,1 15,18H9A1,1 0 0,1 8,17V14.74C6.19,13.47 5,11.38 5,9A7,7 0 0,1 12,2M9,21V20H15V21A1,1 0 0,1 14,22H10A1,1 0 0,1 9,21M12,4A5,5 0 0,0 7,9C7,11.05 8.23,12.81 10,13.58V16H14V13.58C15.77,12.81 17,11.05 17,9A5,5 0 0,0 12,4Z" />
                    </svg>
                </span>
            </div>
        </nav>
        <div class="min-w-[20rem] w-[40%] flex flex-col justify-center items-center bordder border-red-500">
            <div>
                {{ nowDate }}
            </div>
            <div class="text-[4rem] font-bold">
                {{ nowTime }}
            </div>
            <form @submit.prevent="setAlarm()" class="w-full flex flex-col gap-8">

                <div class="flex flex-col">
                    <p>Définir l'heure de l'alarme</p>
                    <div class="flex justify-between text-[1rem]">
                        <div class="w-[48%]">
                            <label for="heure">
                                Heures
                            </label>
                            <select name="heure" id="heure" v-model="heure"
                                class="w-full rounded shadow-sm border-gray-200 text-black" required>
                                <option value="00">00</option>
                                <option value="01">01</option>
                                <option value="02">02</option>
                                <option value="03">03</option>
                                <option value="04">04</option>
                                <option value="05">05</option>
                                <option value="06">06</option>
                                <option value="07">07</option>
                                <option value="08">08</option>
                                <option value="09">09</option>
                                <option value="10">10</option>
                                <option value="11">11</option>
                                <option value="12">12</option>
                                <option value="13">13</option>
                                <option value="14">14</option>
                                <option value="15">15</option>
                                <option value="16">16</option>
                                <option value="17">17</option>
                                <option value="18">18</option>
                                <option value="19">19</option>
                                <option value="20">20</option>
                                <option value="21">21</option>
                                <option value="22">22</option>
                                <option value="23">23</option>
                            </select>
                        </div>
                        <div class="w-[48%]">
                            <label for="minute">
                                Minutes
                            </label>
                            <select name="minute" id="minute" v-model="minute"
                                class="w-full rounded shadow-sm border-gray-200 text-black" required>
                                <option value="00">00</option>
                                <option value="01">01</option>
                                <option value="02">02</option>
                                <option value="03">03</option>
                                <option value="04">04</option>
                                <option value="05">05</option>
                                <option value="06">06</option>
                                <option value="07">07</option>
                                <option value="08">08</option>
                                <option value="09">09</option>
                                <option value="10">10</option>
                                <option value="11">11</option>
                                <option value="12">12</option>
                                <option value="13">13</option>
                                <option value="14">14</option>
                                <option value="15">15</option>
                                <option value="16">16</option>
                                <option value="17">17</option>
                                <option value="18">18</option>
                                <option value="19">19</option>
                                <option value="20">20</option>
                                <option value="21">21</option>
                                <option value="22">22</option>
                                <option value="23">23</option>
                                <option value="24">24</option>
                                <option value="25">25</option>
                                <option value="26">26</option>
                                <option value="27">27</option>
                                <option value="28">28</option>
                                <option value="29">29</option>
                                <option value="30">30</option>
                                <option value="31">31</option>
                                <option value="32">32</option>
                                <option value="33">33</option>
                                <option value="34">34</option>
                                <option value="35">35</option>
                                <option value="36">36</option>
                                <option value="37">37</option>
                                <option value="38">38</option>
                                <option value="39">39</option>
                                <option value="40">40</option>
                                <option value="41">41</option>
                                <option value="42">42</option>
                                <option value="43">43</option>
                                <option value="44">44</option>
                                <option value="45">45</option>
                                <option value="46">46</option>
                                <option value="47">47</option>
                                <option value="48">48</option>
                                <option value="49">49</option>
                                <option value="50">50</option>
                                <option value="51">51</option>
                                <option value="52">52</option>
                                <option value="53">53</option>
                                <option value="54">54</option>
                                <option value="55">55</option>
                                <option value="56">56</option>
                                <option value="57">57</option>
                                <option value="58">58</option>
                                <option value="59">59</option>
                            </select>
                        </div>
                    </div>
                </div>

                <div class="flex flex-col gap-8">
                    <div>
                        <p>Son de l'alarme</p>
                        <div class="">
                            <select name="ringtone" id="ringtone"
                                class="w-full rounded shadow-sm border-gray-200 text-black" required>
                                <option value="00">Ring</option>
                            </select>
                        </div>
                    </div>
                    <div>
                        <p>Nom de l'alarme</p>
                        <div class="">
                            <input name="alarmName" id="alarmName" v-model="alarmName"
                                class="w-full rounded shadow-sm border-gray-200 text-black" required />
                        </div>
                    </div>
                </div>

                <div class="flex flex-col gap-8 mt-8">
                    <button type="submit" id="btn" class="border py-2 bg-blue-600 text-white">Régler une alarme</button>
                </div>

            </form>
        </div>

        <!-- Imported files -->
        <div class="min-w-[20rem] w-[40%]">
            <Rreveilenligne v-if="reveilSwitch" class="" :heure="heure" :minute="minute" :alarmName="alarmName" />
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            alarmName: null,
            heure: null,
            minute: null,
            timeRunner: null,
            reveilSwitch: false
        }
    },
    methods: {
        setAlarm() {
            let time = new Date();
            let hrs = time.getHours();
            let mins = time.getMinutes();
            let secs = time.getSeconds();


            if (heure == '' || heure == undefined) {
                alert("Veuillez renseigner le temps du réveil");
            } else {
                this.reveilSwitch = true
            }
        }
    },
    mounted() {
        this.alarmName = "Alarme";
    }
}
</script>
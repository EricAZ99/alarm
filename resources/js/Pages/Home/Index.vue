<script setup>
</script>

<template>
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
                        <select name="ringtone" id="ringtone" class="w-full rounded shadow-sm border-gray-200 text-black"
                            required>
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
</template>
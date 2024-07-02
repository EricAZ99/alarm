<script setup>
const props = defineProps({
    heure: Number,
    minute: Number,
    alarmName: String
})
</script>

<template>
    <div class="fixed right-0 left-0 top-0 bottom-0 bg-[#f2f7ff] flex justify-center">
        <div class="min-w-[20rem] w-[40%] bordser border-red-500 flex flex-col items-center">
            <div
                class="w-[60%] aspect-square rounded-full border-[.6rem] border-red-500 flex flex-col justify-center items-center">
                <h2>{{ alarmName }}</h2>
                <div class="text-[6rem] flex items-center justify-center">
                    <span>{{ heure }}</span>
                    <span class="animate-pulse">:</span>
                    <span>{{ minute }}</span>
                </div>
            </div>
        </div>

    </div>
</template>
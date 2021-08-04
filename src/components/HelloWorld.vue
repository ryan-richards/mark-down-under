<template>

<div class="container p-4">

        <div v-for="day in days" :key="day.id">
         <div class="buttons" style="padding-bottom:0.5rem;">
            <button v-on:click="day.visible = !day.visible" class="button is-large is-fullwidth">{{day.day}}</button>
        </div>
        <div v-if="day.visible & Date.now() > new Date(day.date_available)" class="card" style="transition: all 0.2s ease;">
            <div v-if="day.img">
                <img style="border-radius:15px" v-bind:src="day.img">
            </div>
            <div id="days" class="container">
                <p>{{day.message}}</p>
            </div>
            <div v-if="day.audio">
                <audio controls>
                    <source v-bind:src="day.audio"/>
                </audio>
            </div>
        </div>
    </div> 

</div>




</template>

<script>

import { supabase } from "../supabase"

export default {
    el: '#days',
    data() {
        return {
            days:[],
        };
    },
    async mounted() {
    const { data, error } = await supabase.from('14days').select('*')
    console.log(data);
    if(error) {
        console.error(error);
    } else {
        this.days = data;
    }
    }
}

</script>

<style>

</style>

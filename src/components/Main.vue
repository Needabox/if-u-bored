<template>
    <div class="flex items-center justify-center px-5 py-5">
        <div class="w-full mx-auto rounded-lg bg-white shadow-lg px-5 pt-5 pb-10 text-gray-800" style="max-width: 500px">
            <div class="w-full mb-10">
                <div class="text-3xl text-indigo-500 text-left leading-tight h-3">“</div>
                <img v-if="loading" src="https://mir-s3-cdn-cf.behance.net/project_modules/max_632/04de2e31234507.564a1d23645bf.gif" class="w-4/12 mx-auto" alt="">
                <p class="text-3xl text-gray-600 text-center px-5">{{ bored.activity }}</p>
                <div class="text-3xl text-indigo-500 text-right leading-tight h-3 -mt-3">”</div>
            </div>
            <div class="w-full">
                <p class="text-lg text-indigo-500 font-bold text-center uppercase">{{ bored.type }}</p>
                <p class="text-xs text-gray-500 text-center">Needabox</p>
            </div>
        </div>
    </div>
    <div class="flex items-center justify-center">
        <button class="bg-red-500 hover:bg-red-700 text-white font-bold py-2 px-10 rounded" @click="GetActivity">
            Do Something Here
        </button>
    </div>
    <MainList :activities="activities" />
</template>

<script>
import MainList from '@/components/MainList.vue'
import axios from 'axios'

export default {
    name: 'Main',
    components: {
        MainList,
    },
    data(){
        return {
            loading: false,
            bored: {
                activity: '',
                type: 'Enjoy this :)',
            },
            activities : []
        }
    },
    methods: {
    async GetActivity(){
            if (this.bored.activity) {
                this.activities = [...this.activities, this.bored];
            }

            this.loading = true;
            this.bored = {
                activity: '',
                type: 'Please Wait...',
            }
            const response = await axios.get('http://www.boredapi.com/api/activity');
            this.loading = false
            this.bored = {
                activity: response.data.activity,
                type: response.data.type,
            }
        }
    }
}
</script>

<style>

</style>
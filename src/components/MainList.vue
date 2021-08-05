<template>
    <div class="flex items-center justify-center mt-10">
    <div class="container"> 
        <div class="flex justify-center">
                <div class="bg-white shadow-xl rounded-lg w-1/2 md:w-2/6">
                    <ul class="divide-y divide-gray-300" v-for="item in activities" :key="item">
                        <li class="p-4 hover:bg-gray-50 cursor-pointer ">{{ item.activity }}</li>
                    </ul>
                </div>
            </div>
    </div>
</div>
</template>

<script>
export default {
    props : ['activities']
}
</script>

<style>

</style>
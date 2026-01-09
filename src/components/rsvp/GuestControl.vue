<template>
    <ul class="list-none flex p-0 my-2 mx-0">
        <li class="my-0 mx-4 border border-solid border-[#ccc] p-4 flex justify-center items-center" :class="{active: activateOption === 'yes'}"><button type="button" class="font-[inherit] bg-transparent border-none cursor-pointer " @click="activate('yes')">Yes</button></li>
        <li class="my-0 mx-4 border border-solid border-[#ccc] p-4 flex justify-center items-center" :class="{active: activateOption === 'no'}"><button type="button" class="font-[inherit] bg-transparent border-none cursor-pointer" @click="activate('no')">No</button></li>
    </ul>
</template>

<script>
    export default{
        props:['modelValue'],
        emits: ['update:modelValue'],
        computed:{
            activateOption(){
                return this.modelValue
            }
        },
        methods: {
            activate(option){
                this.$emit('update:modelValue', option)
            }
        }
    }
</script>

<style scoped>
    .active{
        border: 1px solid #a7125f;
    }
    .active button {
        color: #a7125f;
    }
</style>
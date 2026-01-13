<template>
    <li class="my-4 mx-0 border border-solid border-[#ccc] p-4">
        <p><span class="font-bold">Full Name : </span><span>{{ result.firstname }}</span> <span> {{ result.lastname }}</span></p>
        <p><span class="font-bold">Age : </span><span>{{ result.age }}</span></p>   
        <p><span class="font-bold">Are you Attending?  </span><span>{{ result.attending }}</span></p>   
        <p><span class="font-bold">Selected Meal : </span><span>{{ result.meal }}</span></p>   
        <p><span class="font-bold">Are you bringing guests?  </span><span>{{ result.extraguest }}</span></p> 
        <p><span class="font-bold">Are you bringing gift?  </span><span>{{ result.gift }}</span></p>   
    </li>
</template>

<script>
    export default {
        props: ['result']
    }
</script>
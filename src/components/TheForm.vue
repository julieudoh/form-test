<template>
    <form @submit.prevent="submitForm" class="max-w-2xl p-8 mx-2 rounded-xl shadow-[0_2px_8px_rgba(3,33,73,0.26)] bg-white mb-8 md:mx-auto ">
        <div class="my-3 mx-0">
            <div>
                <label for="first-name" class="font-bold ">First Name <span class="text-red-500">*</span></label>
                <input type="text" id="first-name" name="first-name" class="border border-gray-300 p-2 w-full block mt-2 font-[inherit] " v-model="firstName">
            </div>
            <div>
                <label for="last-name" class="font-bold">Last Name <span class="text-red-500">*</span></label>
                <input type="text" id="last-name" name="last-name" class="border border-gray-300 p-2 w-full block mt-2 font-[inherit]" v-model="lastName">
            </div>
        </div>
        <div class="my-3 mx-0">
            <label for="age" class="font-bold">Age <span class="text-red-500">*</span></label>
            <input type="number" id="age" name="age" v-model="userAge" ref="ageInput" class="border border-gray-300 p-2 w-full block mt-2 font-[inherit]">
        </div>
        <div class="my-3 mx-0">
            <h2 class="text-base my-2 mx-0 font-bold">Are you attending? <span class="text-red-500">*</span></h2>
            <div>
                <input type="radio" name="attending" id="yes" class="inline-block mr-4 w-auto" value="yes" v-model="attendingEvent">
                <label for="yes">Yes</label>
            </div>
            <div>
                <input type="radio" name="attending" id="no" value="no" v-model="attendingEvent" class="inline-block mr-4 w-auto">
                <label for="no">No</label>
            </div>
        </div>
        <div class="my-3 mx-0">
            <h2 class="text-base my-2 mx-0 font-bold">Your meal Selection</h2>
            <div>
                <input type="checkbox" name="meal" id="meal-chicken" value="chicken" v-model="selectedMeal" class="inline-block mr-4 w-auto">
                <label for="meal-chicken">Chicken</label>
            </div>
            <div>
                <input type="checkbox" name="meal" id="meal-fish" value="fish" v-model="selectedMeal" class="inline-block mr-4 w-auto">
                <label for="meal-fish">Fish</label>
            </div>
            <div>
                <input type="checkbox" name="meal" id="meal-salad" value="salad" v-model="selectedMeal" class="inline-block mr-4 w-auto">
                <label for="meal-salad">Salad</label>
            </div>
        </div>
        <div class="my-3 mx-0">
            <label for="guest" class="font-bold block">Are you Attending? <span class="text-red-500">*</span></label>
            <select name="guest" id="guest" v-model="attendingGuest" class="border border-gray-300 p-2 block mt-2 font-[inherit]">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>
        <div class="my-3 mx-0">
            <input type="checkbox" name="confirm-terms" id="confirm-terms" v-model="confirm" class="inline-block mr-4 w-auto">
            <label for="confirm-terms" class="font-bold">Agree to the terms of guest?</label>
        </div>
        <div class="my-3 mx-0">
             <h2 class="text-base my-2 mx-0 font-bold">Are you attending? <span class="text-red-500">*</span></h2>
            <guest-control v-model="extraGuest"></guest-control>
        </div>
        <div>
            <button class="font-[inherit] border border-solid border-[rgb(3,33,73)] bg-[rgb(3,33,73)] text-white cursor-pointer py-3 px-8 text-center rounded-[30px] ">Add Guest</button>
        </div>
    </form>
</template>

<script>
    import GuestControl from './GuestControl.vue';
    export default {
        components: {
            GuestControl
        },
        data(){
            return{
                firstName:'',
                lastName: '',
                userAge: null,
                attendingEvent: null,
                selectedMeal: [],
                attendingGuest: 'yes',
                confirm: false,
                extraGuest: null,
            }
        },
        methods: {
            submitForm(){
                console.log('FirstName: ' + this.firstName);
                this.firstName = '';
                console.log('LastName: ' + this.lastName)
                this.lastName = '';
                console.log('UserAge: ')
                console.log(this.userAge + 5)
                this.userAge = null
                console.log(this.$refs.ageInput.value + 5)
                console.log('Are you attending? ')
                console.log(this.attendingEvent)
                this.attendingEvent = null
                console.log('Your Selected Meal? ')
                console.log(this.selectedMeal)
                console.log(' Are You Attending? ')
                console.log(this.attendingGuest);
                this.attendingGuest = 'yes'
                console.log('Confirm: ' + this.confirm)
                this.confirm = false
                console.log('Bringing A Guest?')
                console.log(this.extraGuest)
                
            }
        }
    }
</script>
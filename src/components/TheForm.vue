<template>
    <form @submit.prevent="submitForm" class="max-w-2xl p-8 mx-2 rounded-xl shadow-[0_2px_8px_rgba(3,33,73,0.26)] bg-white mb-8 md:mx-auto ">
        <div class="my-3 mx-0">
            <div :class="{invalid: firstName === '' && invalidInput}">
                <label for="first-name" class="font-bold ">First Name <span class="text-red-500">*</span></label>
                <input type="text" id="first-name" name="first-name" class="border border-gray-300 p-2 w-full block mt-2 font-[inherit] " v-model.trim="firstName">
                <p v-if="firstName === '' && invalidInput">Please enter a valid name</p>
            </div>
            <div :class="{invalid: lastName === '' && invalidInput}">
                <label for="last-name" class="font-bold">Last Name <span class="text-red-500">*</span></label>
                <input type="text" id="last-name" name="last-name" class="border border-gray-300 p-2 w-full block mt-2 font-[inherit]" v-model.trim="lastName">
                  <p v-if="lastName === '' && invalidInput">Please enter a valid name</p>
            </div>
        </div>
        <div class="my-3 mx-0" :class="{invalid: userAge === null && invalidInput}">
            <label for="age" class="font-bold">Age <span class="text-red-500">*</span></label>
            <input type="number" id="age" name="age" v-model.trim="userAge" ref="ageInput" class="border border-gray-300 p-2 w-full block mt-2 font-[inherit]">
              <p v-if="userAge === null && invalidInput">Please enter a valid name</p>
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
            <p v-if="attendingEvent === false && invalidInput" class="text-red-500">Please select!</p>
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
            <label for="guest" class="font-bold block">Are you bringing a guest? <span class="text-red-500">*</span></label>
            <select name="guest" id="guest" v-model="extraGuest" class="border border-gray-300 p-2 block mt-2 font-[inherit]">
                <option value="yes">Yes</option>
                <option value="no">No</option>
            </select>
        </div>
        <div class="my-3 mx-0">
             <h2 class="text-base my-2 mx-0 font-bold">Are you bringing gifts? <span class="text-red-500">*</span></h2>
            <guest-control v-model="gift"></guest-control>
        </div>
        <div class="my-3 mx-0">
            <input type="checkbox" name="confirm-terms" id="confirm-terms" v-model="confirm" class="inline-block mr-4 w-auto">
            <label for="confirm-terms" class="font-bold">Agree to the terms of guest?</label>
            <p v-if="confirm === false && invalidInput" class="text-red-500">Please agree to terms!</p>
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
                attendingEvent: false,
                selectedMeal: [],
                extraGuest: 'yes',
                confirm: false,
                gift: false,
                invalidInput: false,

            }
        },
        methods: {
            submitForm(){
                if(this.firstName === '' || this.lastName === '' || this.userAge === null || this.attendingEvent === false || this.confirm === false || this.gift === false ){
                    this.invalidInput = true
                    return
                }
                this.invalidInput = false
            
                fetch('https://rsvp-form-34302-default-rtdb.firebaseio.com/rsvpguests.json', {
                    method: 'POST',
                    headers: {
                        'Content-Type': 'application/json'
                    },
                    body: JSON.stringify({firstname: this.firstName, lastname: this.lastName, age: this.userAge, attending: this.attendingEvent, meal: this.selectedMeal, extraguest: this.extraGuest, gift: this.gift, confirmterms: this.confirm})
                })
              


                // fetch('https://rsvp-form-34302-default-rtdb.firebaseio.com/users.json', {
                //     method:'POST',
                //     headers: {'Content-Type': 'application/json'},
                //     body: {
                //         firstname: this.firstName,
                //         lastname: this.lastName,
                //         userage: this.userAge,
                //         attending: this.attendingEvent,
                //         meals: this.selectedMeal,
                //         addedguest: this.extraGuest,
                //         aggreement: this.confirm,
                //         gift: this.gift
                //     }
                // });

                this.firstName = '';
                this.lastName = '';
                this.userAge = null;
                this.attendingEvent = false;
                this.selectedMeal = [];
                this.extraGuest = 'yes';
                this.confirm = false;
                this.gift = false;
                
            }, 
            
        }
    }
</script>

<style scoped>
    .invalid input{
         border-color: red;
    }
    .invalid label {
        color: red;
    }
</style>
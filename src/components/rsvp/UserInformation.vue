<template>
    <base-card>
        <h2 class="text-[#032149] text-center font-bold pb-2 text-xl">Submitted RSVP</h2>
        <div class="flex justify-center items-center">
            <base-button @click="showUserResult" class="text-white">Load Submitted Rsvps</base-button>
        </div>

        <ul class="list-none m-0 p-0">
            <p v-if="isLoading" class="mt-8 font-bold">Loading...</p>
            <p v-else-if="!isLoading && error" class="mt-8 text-center font-bold">{{ error }}</p>
            <p v-else-if="!isLoading && (!results || results.length === 0)" class="mt-8 text-center font-bold">There is no available data for Rvps guest - Please fill in the form.</p>
            <rsvp-result  v-else-if="!isLoading && results && results.length > 0"
            v-for="result in results" :key="result.id" 
            :result="result"></rsvp-result>
        </ul>
    </base-card>
</template>

<script>
    import RsvpResult from './RsvpResult.vue';

    export default {
        
        data(){
            return{
                results: [],
                isLoading: false,
                error: null,
            }
        },
        components: {
            RsvpResult
        },
        methods: {
            showUserResult(){
                this.isLoading = true;
                this.error = null;
                fetch('https://rsvp-form-34302-default-rtdb.firebaseio.com/rsvpguests.json')
                .then((Response) => {
                    if(Response.ok){
                        return Response.json() 
                    }
                })
                .then((data) => {
                    const results = [];
                    this.isLoading = false;
                    for(const id in data) {
                        results.push({
                            id: id,
                            firstname: data[id].firstname,
                            lastname: data[id].lastname,
                            age: data[id].age,
                            attending:data[id].attending,
                            extraguest: data[id].extraguest,
                            gift: data[id].gift,
                            confirmterms: data[id].confirmterms,
                            meal: data[id].meal
                        })
                    }
                    this.results = results;
                })
                .catch((error) => {
                    console.log(error)
                    this.isLoading = false
                    this.error = 'Failed to Fetch data - Please try again later!!'
                })
            }
        }
    }
</script>

<template>
    <div class=" bg-green-200 p-10 min-h-screen">
        <h1 class=" text-green-800 text-center text-4xl mt-10 mb-5">My to do App</h1>
        <form class="flex justify-center" @submit.prevent="addActivity(activity)">
            <input type="text" class=" w-2/5 rounded-l py-2 px-4 outline-none focus:bg-green-300 text-green-800" v-model="activity">
            <button id="activity" class=" bg-green-800 rounded-r py-2 px-4 text-green-200 border-none hover:bg-green-700 transition ease-in duration-75" >Add Activity</button>
        </form>
        <div v-if="empty" class="flex justify-center">
           <p class="text-xl text-red-500"> Please type in an activity.</p>
       </div>
        
       <div v-if="activitiesToDo.length > 0" class="p-5">
            <div v-for="(activity, index) in activitiesToDo" :key="index" class=" flex justify-center">
                <div class=" px-4 py-2 bg-green-500 mb-5 w-3/5 flex justify-between rounded items-center">
                    <p class=" text-xl text-green-800"> {{ index + 1}}: {{ activity }}</p> 
                    <button class=" bg-green-800 rounded py-2 px-4 text-green-200 border-none self-center focus:outline-none hover:bg-green-700 transition ease-in duration-75" @click="deleteActivity(activity)">Delete</button>
                </div>
            </div>
       </div>
    </div>
</template>

<script>
export default {
    name: 'App',
    data(){
        return {
            empty: false,
            activity: "",
            activitiesToDo: [],
        }
    },
    methods: {
        addActivity (activity) {
            if(activity){
                this.activitiesToDo.push(activity)
                this.activity = ''
                this.empty = false
            }else {
                this.empty = true
            }
            
        },
        deleteActivity(activityToDelete) {
            this.activitiesToDo = this.activitiesToDo.filter(activity => {
                return activity !== activityToDelete
            })
        }
    }
}
</script> 
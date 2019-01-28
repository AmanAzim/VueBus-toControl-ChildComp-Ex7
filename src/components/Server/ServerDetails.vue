<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="serverStatus.length==0">Server Details are currently not updated</p>
        <p v-else>Server Status: {{serverStatus}} <br>
                  <button @click="changeStatus">Change Status</button>
        </p>
    </div>

</template>

<script>
    import {eventBus} from "../../main";
    export default {
        data:function () {
            return{
              serverStatus:'',
            };
        },
        created(){
            eventBus.$on('transmit-status', (status)=>{ this.serverStatus=status; });
        },
        methods:{
            changeStatus(){
                this.serverStatus='Good';
                eventBus.$emit('changed-status', this.serverStatus); //This is not needed because server status in an object type so changing it in any component will be ill be counted as global because every component as the pointer to of its direct memory location
            }
        }
    }
</script>

<style>

</style>

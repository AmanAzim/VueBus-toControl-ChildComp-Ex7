<template>
    <div class="col-xs-12 col-sm-6">
        <p v-if="!server">Server Details are currently not updated</p>
        <p v-else>Server #{{server.id}} Server Status: {{server.status}} <br>
            <button @click="changeStatus">Change Status</button>
        </p>
    </div>

</template>

<script>
    import {eventBus} from "../../main";
    export default {
        data:function () {
            return{
              server:null,
            };
        },
        created(){
            eventBus.$on('transmit-status', (server)=>{ this.server=server; });
        },
        methods:{
            changeStatus(){
                this.server.status='Good';
                eventBus.$emit('changed-status', this.server); //This is not needed because server status in an object type so changing it in any component will be ill be counted as global because every component as the pointer to of its direct memory location
            }
        }
    }
</script>

<style>

</style>

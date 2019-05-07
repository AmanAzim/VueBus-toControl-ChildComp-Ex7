<template>
    <div class="col-xs-12 col-sm-6">
        <ul class="list-group">
            <li class="list-group-item" style="cursor: pointer"
                    v-for="server in servers"
                    v-on:click="showDetail(server)"
                     >Server #{{ server.id }}
            </li>
        </ul>
    </div>
</template>

<script>
    import {eventBus} from "../../main";

    export default{
        data:function () {
            return{
                servers:[
                    {id:1, status:'Normal'},
                    {id:2, status:'Critical'},
                    {id:3, status:'Unknown'},
                    {id:4, status:'Normal'}
                ],

            };
        },
        methods:{
            showDetail(server){
                eventBus.$emit('transmit-status', server);
            },
        },
        created(){
            //eventBus.$on('changed-status', (server)=>{ this.servers.status=newStatus;} );
        }
    }
</script>

<style>

</style>

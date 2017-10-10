<template>
    <div class="chat-composer">
        <input type="text" placeholder="type here..." v-model="inputFieldText" @keydown.enter="sendMessage"/>
        <button class="btn btn-primary" @click="sendMessage">send</button>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                inputFieldText: ''
            }
        },
        methods: {
            sendMessage(){
                this.$emit('sending-message',{
                    message: this.inputFieldText,
                    user:{
                        name: $('.navbar-right .dropdown-toggle').text()
                    }
                });
                this.inputFieldText='';
            }
        }
    }
</script>

<style lang="css">
    .chat-composer {
        display: flex;
    }

    .chat-composer input {
        flex: 1 auto;
    }

    .chat-composer button {
        border-radius: 0;
    }

</style>
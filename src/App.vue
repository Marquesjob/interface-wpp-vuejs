<template>

    <div>
        <section class="section">
            <div class="container">
                <div class="columns">

                    <div class="column is-3 lista-de-conversas">
                        <div class="barra-superior" />
                        <div class="item" v-for="(conversa, index) in conversas" v-on:click="activeIndex = index"
                            v-bind:key="index">
                            <div class="title is-6">{{ conversa.user }}</div>
                            <div class="subtitle is-6">Última mensagem...</div>
                        </div>
                    </div>

                    <div class="column conversa-ativa">

                        <div class="barra-superior">
                            <span>{{ conversas[activeIndex].user }}</span>
                        </div>
                        
                        <div class="lista-mensagens">

                            <Message v-for="(message, index) in conversas[activeIndex].messages"
                            v-bind:key="index" 
                            :content="message.content" 
                            :time="message.time" 
                            :hostMessage="message.hostMessage"
                            />

                        </div>

                        <div class="barra-inferior">
                            <input v-model="newMessage" v-on:keyup.enter="sendMessage" type="text" class="input" placeholder="Insira sua mensagem">
                        </div>

                    </div>

                </div>
            </div>
        </section>
    </div>

</template>

<script>

import chats from './dataChats.js'
import Message from './Message.vue'

export default {

    data: () => {
        return {
            conversas: chats,
            activeIndex: 0,
            newMessage: ''
        }
    },

    components: {
        Message
    },

    methods: {
        sendMessage: function () {
        
           let currentTime = new Date().getHours() + ":" + new Date().getMinutes();
           let Message =  {
            time: currentTime,
            content: this.newMessage,
            hostMessage: true
           }

           this.conversas[this.activeIndex]
           .messages
           .push(Message);

           this.newMessage = "";
        }
    }

}


</script>


<style>

.barra-inferior {
    bottom: 0;
    width: 64.2em;
    padding: 10px;
    position: absolute;
    background: #f0f0f0;
}

.barra-inferior input {
    border: none;
    padding: 10px;
    margin: 0 50px;
    width: 90%;
    border-radius: 15px;
    font-size: 16px;
}

.lista-mensagens {
    height: 85%;
    display: flex;
    justify-content: flex-end;
    flex-direction: column;
    padding-bottom: 10px;
}

.columns {
    min-height: 850px;
    box-shadow: 0 3rem 3rem -1rem rgba(10, 10, 10, .2);
}

.column {
    padding: 0;
}

.lista-de-conversas {
    background: white;
}

.conversa-ativa {
    background: #E5DDD5;
}

.barra-superior {
    margin: 0;
    height: 60px;
    background: #f0f2f5;
    border-right: 1px solid #E1E1E1;

}

.barra-superior span {
    line-height: 60px;
    margin-left: 25px;
    font-weight: 500;
}

.item {
    border-bottom: 1px solid #F2F2F2;
    padding: 15px 30px;
    margin-bottom: 0 !important;
}

.item:hover {
    background: #f0f1f3;
    cursor: pointer;
}

.subtitle {
    color: #858585;
}

</style>



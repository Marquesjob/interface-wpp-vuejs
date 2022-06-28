<template>
    <div class="mensagem" :class="{host: hostMessage}">{{ content }}
        <span>{{ time }}</span>
    </div>
</template>


<script>
    export default {
        props: ['content', 'time', 'hostMessage']
    }
</script>

<style>

    .mensagem {
        font-size: 14px;
        box-shadow: rgba(0,0,0,0.13) 0px 1px 0.5px 0px;
        background: white;
        margin: 5px 100px;
        padding: 5px 10px;
        border-radius: 5px;
        width: fit-content;
    }

    .mensagem span {
        margin-left: 25px;
        font-size: 11px;
        color: gray;
    }

    .host {
        background: rgb(228 242 217) !important;
        align-self: flex-end;
    }


</style>    
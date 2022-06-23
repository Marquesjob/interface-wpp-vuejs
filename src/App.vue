<template>
    <div>
        <section class="section">
            <div class="container">
                <div class="columns">

                    <div class="column is-3 lista-de-conversas">
                        <div class="barra-superior" />
                        <p v-for="conversa in conversas">{{ conversa.usuario }}</p>
                    </div>

                    <div class="column conversa-ativa">
                        <div class="barra-superior">
                            <span>Usuário</span>
                        </div>
                    </div>

                </div>
            </div>
        </section>
    </div>
</template>

<script>
    import chats from './dataChats.js'
    export default {
        data: () => {
            return {
                conversas: chats
            }
        }
    }

</script>


<style>

    .columns {
         min-height: 800px;
         box-shadow: 0 3rem 3rem -1rem rgba(10, 10, 10,.2);
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

</style>



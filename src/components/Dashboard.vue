<template>
    <div class="burger-table">
        <div>
            <div id="burger-table-heading">
                <div class="order-id">#:</div>
                <div>Cliente:</div>
                <div>Pão:</div>
                <div>Opcionais:</div>
                <div>Ações:</div>
            </div>
            <div class="burger-table-rws">
                <div class="burger-table-row" v-for="burger in burgers" :key="burgers.id">
                    <div class="order-number">{{ burger.id }}</div>
                    <div>{{ burger.nome }}</div>
                    <div>{{ burger.pao }}</div>
                    <div>{{ burger.carne }}</div>
                    <div>
                        <ul>
                            <li v-for="(opcional, index) in burger.opcionais" :key="index" >
                                {{ opcional }}
                            </li>
                        </ul>
                    </div>
                    <select name="status" class="status" @change="updateBurger($event, burger.id)">
                        <option value="">Status</option>
                        <option v-for="s in status" :key="s.id" :value="s.tipo" :selected="burger.status == s.tipo">
                        {{ s.tipo }}
                        </option>
                    </select>
                    <button class="delete-bnt" @click="deleteBurger(burger.id)">Cancelar</button>
                </div>    
            </div>
        </div>
    </div>

</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue';

const burgers = ref()
const burger_id = ref()
const status = ref()

const getPedidos = async () => {
    const req = await fetch('http://localhost:3000/burgers')
    const data = await req.json()
    burgers.value = data

    getStatus()
    
}

const getStatus = async () => {
    const req = await fetch('http://localhost:3000/status')
    const date = await req.json()
    status.value = date
}

const deleteBurger = async (id:number) => {
    const req = await fetch(`http://localhost:3000/burgers/${id}`, { method: 'DELETE' })
    const res = await req.json()
    getPedidos()
}

const updateBurger = async (event:any, id:number) => {
    const option = event.target.value
    const dateJson = JSON.stringify({ status: option })
    const req = await fetch(`http://localhost:3000/burgers/${id}`, { 
        method: 'PATCH',
        headers: { 'content-Type': 'application/json' },
        body: dateJson
    })
    const res = await req.json()
    console.log(res)    
}

onMounted(() => {
    getPedidos()
})

</script>

<style scoped>
#burger-table-heading,
#burger-table-rows,
.burger-table-row{
    display: flex;
    flex-wrap: wrap;
}

#burger-table-heading{
    font-weight: bold;
    padding: 12px;
    border-bottom: 3px solid #333;
}

#burger-table-heading div,
.burger-table-row div{
    width: 18%;
}

.burger-table-row{
    width: 100%;
    padding: 12px;
    border-bottom: 1px solid #ccc;
}

#burger-table-heading .order-id,
.burger-table-row .order-number{
    width: 5%;
}

select{
    padding: 12 px 16px;
    margin-right: 12px;
}

.delete-bnt{
    background-color: #222;
    color: #fcba03;
    font-weight: bold;
    border: 2px solid #222;
    padding: 10px;
    font-size: 16px;
    margin: 0 auto;
    cursor: pointer;
    transition:  .5s;
}

.delete-bnt :hover{
    background-color: transparent;
    -ms-text-combine-horizontal: #222;
}



</style>
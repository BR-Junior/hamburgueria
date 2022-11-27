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
                <div class="burger-table-row">
                    <div class="order-number">1</div>
                    <div>nome</div>
                    <div>pão</div>
                    <div>carne</div>
                    <div>
                        <ul>
                            <li>ops</li>
                            <li>ops</li>
                        </ul>
                    </div>
                    <select name="status" id="status">
                        <option value="">Status</option>
                    </select>
                    <button class="delete-bnt">Cancelar</button>
                </div>    
            </div>
        </div>
    </div>

</template>

<script setup lang="ts">

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
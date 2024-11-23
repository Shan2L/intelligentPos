<script setup>
import Infolist from './Infolist.vue';
import Status from './Status.vue'
</script>

<template>
    <div id="leftside">
        <div id="good-id">
            <text class="input-text">商品条码：</text><input id="input" placeholder="输入商品条形码">
        </div>

        <Infolist></Infolist>
        <Status></Status>

    </div>

</template>

<style scoped>
#leftside {
    display: flex;
    flex-direction: column;
    border: 2px solid black;
    padding: 1em;
    height: 96%;
    width: 100%;
    justify-content: space-between;
}

#good-id {
    display: flex;
    height: 10%;
    width: 100%;
    align-items: center;
    margin-top: 1em;
    justify-content: space-between;
}

#input {
    width: 70%;
    height: 80%;
    font-size: 2em;
    margin-left: 0.5em;
    border: 1px solid #0c0c0c;
    border-radius: 0.2em;
    background-color: #e8dede;
    padding-left: 1em;
}
.input-text {
    font-size: 2.5em;
}

.text {
    font-size: 2.5em;
    text-align: left;
}

#status {
    width: 100%;
    height: 10%;
    display: flex;
    justify-content: space-between;
}
</style>
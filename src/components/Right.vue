<script setup>
import { ref } from 'vue'
const MAX_QUANTUM = 999;
const MIN_QUANTUM = 0;

const shopping_list = ref([
    { id: 0, name: '茶叶', price: '10', quantity: 1000 },
    { id: 1, name: '咖啡', price: '20', quantity: 15 },
    { id: 2, name: '牛奶', price: '12', quantity: 30 },
    { id: 3, name: '矿泉水', price: '5', quantity: 50 },
    { id: 4, name: '苹果', price: '8', quantity: 25 },
    { id: 5, name: '橙子', price: '10', quantity: 20 },
    { id: 6, name: '香蕉', price: '7', quantity: 18 },
    { id: 7, name: '葡萄', price: '15', quantity: 12 },
    { id: 8, name: '草莓', price: '25', quantity: 8 },
    { id: 9, name: '鸡蛋', price: '6', quantity: 40 },
    { id: 10, name: '面包', price: '10', quantity: 20 },
    { id: 11, name: '饼干', price: '8', quantity: 35 },
    { id: 12, name: '巧克力', price: '18', quantity: 10 },
    { id: 13, name: '薯片', price: '15', quantity: 14 },
    { id: 14, name: '泡面', price: '4', quantity: 50 },
    { id: 15, name: '调味料', price: '6', quantity: 18 },
    { id: 16, name: '牛肉', price: '30', quantity: 5 },
    { id: 17, name: '猪肉', price: '25', quantity: 10 },
    { id: 18, name: '鸡肉', price: '20', quantity: 8 },
    { id: 19, name: '鱼肉', price: '28', quantity: 6 },
    { id: 20, name: '虾', price: '35', quantity: 4 },
    { id: 21, name: '鱿鱼', price: '40', quantity: 3 },
    { id: 22, name: '大米', price: '50', quantity: 1 },
    { id: 23, name: '面粉', price: '45', quantity: 2 },
    { id: 24, name: '油', price: '70', quantity: 2 },
    { id: 25, name: '盐', price: '2', quantity: 50 },
    { id: 26, name: '糖', price: '3', quantity: 40 },
    { id: 27, name: '酱油', price: '5', quantity: 30 },
    { id: 28, name: '醋', price: '6', quantity: 25 },
    { id: 29, name: '奶粉', price: '60', quantity: 5 },
    { id: 30, name: '果汁', price: '12', quantity: 10 },
    { id: 31, name: '啤酒', price: '15', quantity: 18 },
    { id: 32, name: '红酒asdasdasdasdasdasd', price: '50', quantity: 4 },
    { id: 33, name: '白酒', price: '100', quantity: 2 },
    { id: 34, name: '绿茶', price: '20', quantity: 12 },
    { id: 35, name: '红茶', price: '25', quantity: 10 },
    { id: 36, name: '乌龙茶', price: '30', quantity: 8 },
    { id: 37, name: '果茶', price: '15', quantity: 10 },
    { id: 38, name: '苏打水', price: '10', quantity: 20 },
    { id: 39, name: '椰子水', price: '18', quantity: 8 },
])

function clear_product_item(product)
{
    console.log(product)
    shopping_list.value = shopping_list.value.filter(item => item != product)
}

function clear_shopping_list()
{
    shopping_list.value = []
}

function add_quantum(product)
{
    const item = shopping_list.value.find(item=> item['id'] === product['id'])
    if (item){
        if (item['quantity']+1 > MAX_QUANTUM){
            alert("!!!已经超出了单间商品最大数量，无法继续添加!!!")
        }else{
            item['quantity']++;
        }
    }
    else{
        alter("!!!!没有找到该商品的信息!!!")
    }
}

function minus_quantum(product)
{
    const item = shopping_list.value.find(item=> item['id'] === product['id'])
    if (item){
        if (item['quantity'] -1 <= MIN_QUANTUM)
        {
            clear_product_item(product)
        }else{
            item['quantity']--;
        }
    }
    else{
        alter("!!!没有找到该商品的信息!!!")
    }
}

</script>

<template>

    <div id="rightside">
        <div id="table-title">
            <div class="text_name">名称 </div>
            <div class="text_num">单价 </div>
            <div class="text_num">数量 </div>
            <div class="text_num">总价 </div>
            <div class="del_container">
                <img class="title_del_btn" @click="clear_shopping_list" src="@/assets/actions/delete.png" />
            </div>
        </div>

        <div id="shopping-list">
            <div class="shopping-item" v-for="product in shopping_list">
                <div class="text_name">{{ product.name }}</div>
                <div class="text_num">{{ product.price }}</div>
                <div class="quantum_container">
                    <img class="change_quantum_btn" @click="minus_quantum(product)" src="@/assets/actions/minus.png"/>
                    <div class="text_quantum">{{ product.quantity }}</div>
                    <img class="change_quantum_btn" @click="add_quantum(product)" src="@/assets/actions/add.png"/>
                </div>
                <div class="text_num">{{ product.price * product.quantity }}</div>
                <div class="del_container">
                    <img class="item_del_btn"  @click="clear_product_item(product)"  src="@/assets/actions/delete.png" />
                </div>
            </div>
        </div>

        <div id="summary">
            <div class="summary_text">总计</div>
            <div class="summary_text">2000元</div>
        </div>

    </div>
</template>

<style scoped>
#rightside {
    align-items: center;
    display: flex;
    flex-direction: column;
    width: 100%;
    height: 100%;
}

#table-title {
    height: 5%;
    width: 95%;
    border: 3px solid;
    display: flex;
    align-items: center;
}

#shopping-list {
    display: flex;
    flex-direction: column;
    overflow: auto;
    width: 95%;
    height: 90%;
    border: 3px solid;
}

.shopping-item {
    border: 2px solid;
    width: 97%;
    height: 3.5em;
    display: flex;
    flex-direction: row;
    padding-left: 1em;
}

.text_name {
    font-size: 2em;
    width: 45%;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    border: 3px, solid;
    border-bottom: 0px;
    border-top: 0px;
    border-left: 0px;
    text-align: center;
}

.text_num {
    font-size: 2em;
    width: 20%;
    overflow: hidden;
    white-space: nowrap;
    text-overflow: ellipsis;
    border: 3px, solid;
    border-bottom: 0px;
    border-top: 0px;
    border-left: 0px;
    text-align: center;
}

.summary_text{
    font-size: 2em;
}

.del_container {
    width: 8%;
    height: 100%;
    border: 3px, solid;
    border-bottom: 0px;
    border-top: 0px;
    border-left: 0px;
    display: flex;
    flex-direction: row;
    justify-content: center;
    justify-items: center;
    align-items: center;
}

.quantum_container {
    display: flex;
    width: 23%;
    align-items: center;
    border-right: 3px solid;
    padding-left: 2px;
    padding-right: 2px;
}

.text_quantum {
    width: 60%;
    height: 100%;
    font-size: 2em;
    text-align: center;
    align-items: center;
}

#summary {
    display: flex;
    height: 10%;
    width: 90%;
    font-size: 2em;
}

.title_del_btn{
    width: 60%;
    height: 60%;
}

.item_del_btn {
    width: 60%;
    height: 60%;
}

.item_del_btn:hover {
    width: 60%;
    height: 70%;
}

.change_quantum_btn{
    width: 20%;
    height: 60%;
    border: 1px solid;
}

.change_quantum_btn:hover{
    width: 20%;
    height: 60%;
    border: 3px solid;
}
</style>
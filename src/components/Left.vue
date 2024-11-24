<script setup>
import Status from './Status.vue'
import { ref } from 'vue'
const product_list = ref([
    { id: '6901028090544', name: "盛京", category:"香烟", price: 20, unit: '盒', size: '160mm*90mm*15mm', weight: '0.5 kg', number: 100, checkin_date:"2020-10-4", made_date:"2020-9-9", secure_date:"10 days"},
    { id: '6901028180801', name: "黄鹤楼", category:"香烟", price: 26, unit: '盒', size: '160mm*90mm*15mm', weight: '0.5 kg', number: 100, checkin_date:"2020-10-4", made_date:"2020-9-9", secure_date:"10 days"},
    { id: '6922602231061', name: "蛋卷", category:"食品", price: 20, unit: '盒', size: '160mm*90mm*15mm', weight: '2 kg', number: 100, checkin_date:"2020-10-4", made_date:"2020-9-9", secure_date:"10 days"},
    { id: '6955887980102', name: "川崎火锅底料", category:"食品", price: 5, unit: '碗', size: '160mm*90mm*15mm', weight: '0.1 kg', number: 100, checkin_date:"2020-10-4", made_date:"2020-9-9", secure_date:"10 days"},
    { id: '9787511379399', name: "反本能", category:"书籍", price: 100, unit: '盒', size: '160mm*90mm*15mm', weight: '1 kg', number: 100, checkin_date:"2020-10-4", made_date:"2020-9-9", secure_date:"10 days"},

])

const search_series_id = ref("");
const search_result = ref({ id: 'xxxxxxxxxxxxxxx', 
                            name: "xxx", 
                            category:"xx", 
                            price: "xx", 
                            unit: 'x', 
                            size: 'xxxx', 
                            weight: 'x kg', 
                            number: 'xxx', 
                            checkin_date:"xxxx-xx-xx", 
                            made_date:"xxxx-xx-xx", 
                            secure_date:"xx days"});

function query_product_info() {
    console.log(search_series_id.value)
    const result = product_list.value.find(item => item['id'] === search_series_id.value)
    if (result) {
        console.log(result)
        search_result.value = result;
        search_series_id.value = ""
    } else {
        alert("No product")
        search_result.value = { id: "***********", name: "未查询到信息", price: 0 };
        search_series_id.value = ""
    }
}


</script>

<template>
    <div id="leftside">
        <div id="good-id">
            <div class="input-text">商品条码：</div>
            <input id="input" placeholder="输入商品条形码" v-model="search_series_id"
                v-on:keydown.enter="query_product_info()" />
        </div>

        <div id="info-list">
            <div class="info-item">
                <div class="text">商品名称:&nbsp;</div>
                <div class="text"> {{search_result.name}}</div>
            </div>

            <div class="info-item">
                <div class="text">类别:&nbsp;</div>
                <div class="text">{{search_result.category}}</div>
            </div>

            <div class="info-item">
                <div class="text">规格:&nbsp;</div>
                <div class="text">{{search_result.category}}</div>
            </div>

            <div class="info-item">
                <div class="text">重量:&nbsp;</div>
                <div class="text">{{search_result.weight}}</div>
            </div>
            <div class="info-item">
                <div class="text">库存数量:&nbsp;</div>
                <div class="text">{{search_result.number }}</div>
            </div>
            <div class="info-item">
                <div class="text">单价(盒):&nbsp;</div>
                <div class="text">{{search_result.price}}元</div>
            </div>
            <div class="info-item">
                <div class="text">入库日期:&nbsp;</div>
                <div class="text">{{search_result.checkin_date}}</div>
            </div>
            <div class="info-item">
                <div class="text">生产日期:&nbsp;</div>
                <div class="text">{{ search_result.made_date }}</div>
            </div>
            <div class="info-item">
                <div class="text">保质期:&nbsp;</div>
                <div class="text">{{ search_result.secure_date }}</div>
            </div>
            <div class="info-item">
                <div class="text">过期日期:&nbsp;</div>
                <div class="text">2023-10-20</div>
            </div>
        </div>

        <div id="status">
            <div class="text">查询状态：</div>
            <div>
                <img id="status-logo" src="@/assets/status/success.png"/>
            </div>
        </div>
    </div>
</template>

<style scoped>
#leftside {
    display: flex;
    flex-direction: column;
    border: 2px solid black;
    padding: 1em;
    height: 100%;
    width: 100%;
    /* justify-content: space-between; */
}

#good-id {
    display: flex;
    height: 10%;
    width: 100%;
    align-items: center;
    margin-top: 1em;
    /* justify-content: space-between; */
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
    width: 30%;
}

.text {
    font-size: 2.5em;
    text-align: left;
}


#info-list {
    display: flex;
    flex-direction: column;
    height: 80%;
    width: 100%;
    justify-content: flex-start;
}

.info-item {
    display: flex;
    height: 10%;
    width: 95%;
    align-items: center;
    justify-content: space-between;
}

#status{
    height: 20%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

#status-logo{
    width: 50%;
    height: 50%;
}
</style>
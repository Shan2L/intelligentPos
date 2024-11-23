<script setup>

</script>

<template>
    <div id="info-list">
        <div class="info-item">
            <text class="text">商品名称:&nbsp;</text>
            <text class="text">黄鹤楼</text>
        </div>

        <div class="info-item">
            <text class="text">类别:&nbsp;</text>
            <text class="text">香烟</text>
        </div>

        <div class="info-item">
            <text class="text">规格:&nbsp;</text>
            <text class="text">170mm*100mm*20mm</text>
        </div>

        <div class="info-item">
            <text class="text">重量:&nbsp;</text>
            <text class="text">0.1kg</text>
        </div>
        <div class="info-item">
            <text class="text">库存数量:&nbsp;</text>
            <text class="text">10</text>
        </div>
        <div class="info-item">
            <text class="text">单价(盒):&nbsp;</text>
            <text class="text">20元</text>
        </div>
        <div class="info-item">
            <text class="text">入库日期:&nbsp;</text>
            <text class="text">2024-10-13</text>
        </div>
        <div class="info-item">
            <text class="text">生产日期:&nbsp;</text>
            <text class="text">2023-10-10</text>
        </div>
        <div class="info-item">
            <text class="text">保质期:&nbsp;</text>
            <text class="text">10天</text>
        </div>
        <div class="info-item">
            <text class="text">过期日期:&nbsp;</text>
            <text class="text">2023-10-20</text>
        </div>
    </div>
</template>

<style scoped>

#info-list {
    display: flex;
    flex-direction: column;
    height: 70%;
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

.text {
    font-size: 2.5em;
    text-align: left;
}
</style>
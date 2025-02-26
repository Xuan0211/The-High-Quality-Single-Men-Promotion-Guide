<template>
    <view class="flex-col page space-y-28">
        <view class="self-start group">
            <text class="text">
                图灵班
            </text>
            <text class="text_2">优质单身男性促销指南</text>
        </view>
        <view class="grid">
            <Item v-for="(d,index) in databank" :key="index" :index="index"></Item>
        </view>
    </view>
</template>

<script>
    import Item from "@/componenets/squareItem/squareItem.vue";
    import DataBank from "@/storage/databank.json";
    export default {
        data() {
            return {
                title: 'Hello',
                databank: DataBank.DATABANK
            }
        },
        onLoad() {
            console.log("hello")
            console.log(this.databank)
        },
        methods: {

        },
        components: {
            Item
        }
    }
</script>

<style>
    .page {
        padding: 40rpx 30rpx 0;
        background-color: #fdf7fd;
        width: 100%;
        overflow-y: auto;
        overflow-x: hidden;
        height: 100%;
    }

    .space-y-28>view:not(:first-child),
    .space-y-28>text:not(:first-child),
    .space-y-28>image:not(:first-child) {
        margin-top: 56rpx;
    }

    .group {
        margin-left: 16rpx;
        display: inline-flex;
        flex-direction: column;
        align-items: flex-start;
        width: 600rpx;
    }

    .text {
        color: #e43d34;
        font-size: 72rpx;
        font-family: Microsoft YaHei;
        font-weight: 700;
        line-height: 86rpx;
    }

    .text_2 {
        color: #e43d34;
        font-size: 50rpx;
        font-family: Microsoft YaHei;
        line-height: 60rpx;
        font-weight: 300;
    }

    .grid {
        display: grid;
        grid-template-columns: repeat(2, 1fr);
        row-gap: 20rpx;
        column-gap: 32rpx;
    }
</style>
<template>
    <view>
        <view class="page" @click="tomore">
            <image class="image" mode="aspectFill" :src="databank[index].imgURL" />
            <view class="group">
                <text class="text">{{databank[index].name}}</text>
                <view class="button"><text class="text_2">立即选购</text></view>
            </view>
        </view>
    </view>
</template>

<script>
    import DataBank from "@/storage/databank.json";
    export default {
        name: "squareItem",
        props: {
            index: Number
        },
        data() {
            return {
                databank: DataBank.DATABANK,
            }
        },
        mounted() {},
        methods: {
            tomore() {
                console.log("to more");
                uni.navigateTo({
                    url: `/pages/more/more?index=${this.index}`
                })
            }
        }
    }
</script>

<style>
    .page {
        display: flex;
        padding-bottom: 10rpx;
        padding-top: 3rpx;
        flex-direction: column;
        align-items: center;
        gap: 5px;
        border-radius: 10px;
        background-color: #E43D34;
        width: 320rpx;
    }

    .group {
        display: flex;
        flex-direction: column;
        justify-content: space-between;
        align-items: center;
        gap: 15rpx;
    }

    .text {
        color: #FFF0F0;
        font-family: Microsoft YaHei;
        font-size: 30rpx;
        font-style: normal;
        font-weight: 700;
        line-height: normal;
    }

    .button {
        display: flex;
        padding: 2px 7px;
        justify-content: center;
        align-items: center;
        gap: 10px;
        border-radius: 5px;
        background: linear-gradient(180deg, #FFFA78 0%, #FFA740 100%);
    }

    .text_2 {
        color: #E43D34;
        font-family: Microsoft YaHei;
        font-size: 30rpx;
        font-style: normal;
        font-weight: 700;
        line-height: normal;
    }

    .image {
        width: 320rpx;
        height: 320rpx;
    }
</style>
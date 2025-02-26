<template>
    <view>
        <view class="flex-row items-center list-item space-x-36">
            <view class="flex-row items-center space-x-20">
                <text class="font_2">{{label}}</text>
            </view>
            <text class="font_3">{{content}}</text>
        </view>
    </view>
</template>

<script>
    export default {
        props: {
            label: String,
            content: String,
            imgUrl: String
        },
        data() {
            return {

            }
        },
        methods: {

        }
    }
</script>

<style>
    .list-item {
        padding: 16rpx 32rpx;
        background-color: #fff0f0;
        overflow: hidden;
        border-bottom: solid 2rpx #e7e4e4;
        display: flex;

        align-items: flex-start;
    }

    .space-x-36>view:not(:first-child),
    .space-x-36>text:not(:first-child),
    .space-x-36>image:not(:first-child) {
        margin-left: 30rpx;
    }

    .space-x-20>view:not(:first-child),
    .space-x-20>text:not(:first-child),
    .space-x-20>image:not(:first-child) {
        margin-left: 40rpx;
    }

    .image_3 {
        width: 48rpx;
        height: 48rpx;
    }

    .font_2 {
        font-size: 30rpx;
        font-family: Microsoft YaHei;
        line-height: 29rpx;
        font-weight: 700;
        color: #000000;
        width: 120rpx;
    }

    .font_3 {
        font-size: 28rpx;
        font-family: Microsoft YaHei;
        line-height: 50rpx;
        width: 550rpx;
        color: #000000;
    }
</style>
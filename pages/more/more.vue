<template>
    <view>
        <view class="flex-col relative page">
            <image class="image" :src="databank[index].imgURL" />
            <view class="flex-col section_2">
                <view class="flex-col group space-y-18">
                    <text class="self-start text">{{databank[index].name}}</text>
                    <view class="flex-col items-start">
                        <text class="font_1">{{databank[index].slogan}}</text>
                    </view>
                </view>
                <view class="flex-col section_3 space-y-12">
                    <text class="self-center text_2">宝贝详情</text>
                    <view class="flex-col space-y-10">
                        <image class="image_2"
                            src="https://codefun-proj-user-res-1256085488.cos.ap-guangzhou.myqcloud.com/62f8bcea5a7e3f03100a0ed5/62f8bd5e689f2800114ed71c/16996421559696075212.png" />
                        <view class="flex-col">
                            <ListItem v-for="(d,index1) in databank[index].more" :key="index1" :label="label[index1]"
                                :content="d" :imgUrl="icon[index1]">
                            </ListItem>
                        </view>
                    </view>
                </view>
            </view>
            <view class="flex-col justify-start items-center self-center text-wrapper" @click="show"><text
                    class="text_4">立即购买</text>
            </view>
        </view>
        <view class="input" :style="{'visibility':inputVisible}">
            <textarea class="textarea" placeholder="或许可以留下联系方式~" v-model="input"></textarea>
            <view class="flex-col justify-start items-center self-center text-wrapper" @click="unShow">
                <text class="text_4">发送</text>
            </view>
            <text @click="close">忍痛退出</text>
        </view>
    </view>
</template>

<script>
    import ListItem from "@/componenets/ListItem/ListItem.vue"
    import DataBank from "@/storage/databank.json";
    export default {
        components: {
            ListItem
        },
        data() {
            return {
                databank: DataBank.DATABANK,
                index: 0,
                label: {
                    "MBTI": "MBTI",
                    "hometown": "产地",
                    "introduction": "简介",
                    "star": "星座",
                    "like": "他喜欢",
                    "dating": "攻略指南",
                    "location": "偶遇地点"
                },
                icon: {
                    "MBTI": "https://codefun-proj-user-res-1256085488.cos.ap-guangzhou.myqcloud.com/62f8bcea5a7e3f03100a0ed5/62f8bd5e689f2800114ed71c/16996421559713596336.png"
                },
                inputVisible: "hidden",
                input: undefined
            }
        },
        onLoad: function(option) {
            this.index = option.index;
        },
        methods: {
            show() {
                if (this.databank[this.index].isSold) {
                    uni.showToast({
                        title: "已售罄",
                        icon: "error"
                    })
                } else {
                    this.inputVisible = "visible";
                }

            },
            unShow() {
                if (this.input == undefined) {
                    uni.showToast({
                        title: "请输入内容",
                        icon: "error"
                    });
                }
                const db = uniCloud.database();
                db.collection("contact").add({
                    "forWho": this.databank[this.index].trueName,
                    "content": this.input,
                    "index": this.index.toString()
                }).then((res) => {
                    this.input = undefined;
                    this.inputVisible = "hidden";
                }).catch((err) => {
                    uni.showToast({
                        title: "失败",
                        icon: "error"
                    })
                });

            },
            close() {
                this.input = undefined;
                this.inputVisible = "hidden";
            }
        }
    }
</script>

<style>
    .page {
        padding: 20rpx 0 18rpx;
        background-color: #e43d34;
        width: 100%;
        overflow-y: auto;
        overflow-x: hidden;
        height: 100%;
    }

    .section_2 {
        background-color: #ffffff;
        border-radius: 40rpx 40rpx 0px 0px;
        overflow: hidden;
    }

    .group {
        padding: 56rpx 52rpx 64rpx;
    }

    .space-y-18>view:not(:first-child),
    .space-y-18>text:not(:first-child),
    .space-y-18>image:not(:first-child) {
        margin-top: 36rpx;
    }

    .text {
        color: #000000;
        font-size: 42rpx;
        font-family: Microsoft YaHei;
        font-weight: 700;
        line-height: 32rpx;
    }

    .font_1 {
        font-size: 30rpx;
        font-family: Microsoft YaHei;
        line-height: 36rpx;
        font-weight: 700;
        color: #e43d34;
    }

    .section_3 {
        padding: 36rpx 0 28rpx;
        background-color: #fff0f0;
    }

    .space-y-12>view:not(:first-child),
    .space-y-12>text:not(:first-child),
    .space-y-12>image:not(:first-child) {
        margin-top: 24rpx;
    }

    .text_2 {
        color: #000000;
        font-size: 34rpx;
        font-family: Microsoft YaHei;
        font-weight: 700;
        line-height: 33rpx;
    }

    .space-y-10>view:not(:first-child),
    .space-y-10>text:not(:first-child),
    .space-y-10>image:not(:first-child) {
        margin-top: 20rpx;
    }

    .image_2 {
        width: 750rpx;
        height: 316rpx;
    }

    .text-wrapper {
        margin-top: 18rpx;
        padding: 24rpx 0 16rpx;
        background-image: linear-gradient(180deg, #fff977 0%, #ffa740 100%);
        border-radius: 10rpx;
        overflow: hidden;
        width: 284rpx;
    }

    .text_4 {
        color: #e43d34;
        font-size: 54rpx;
        font-family: Microsoft YaHei;
        font-weight: 700;
        line-height: 53rpx;
    }

    .image {
        background-color: #ffffff;
        overflow: hidden;
        width: 750rpx;
        height: 750rpx;
    }

    .input {
        visibility: hidden;
        position: fixed;
        top: 50%;
        left: 50%;
        margin-top: -300rpx;
        margin-left: -300rpx;
        display: inline-flex;
        width: 600rpx;
        padding: 10px;
        flex-direction: column;
        align-items: center;
        gap: 10px;
        border-radius: 10px;
        background: #FFF0F0;
        box-shadow: 0px 0px 20px 0px rgba(0, 0, 0, 0.25);
    }

    .textarea {
        padding: 10rpx;
        width: 500rpx;
        height: 400rpx;
    }
</style>
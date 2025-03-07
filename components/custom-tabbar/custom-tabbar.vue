<template>
	<view class="tabbar-box">
		<view class="menu-list">
			<view class="item" :style="{color:selIdx==index?hoverColor:color}" v-for="(item,index) in list"
				@click="click(index)" :key="index">
				<view>
					<view class="icon-box">
						<image class="img" :src="selIdx==index?item.selectedIconPath:item.iconPath">
						</image>
					</view>
				</view>
				<text class="label" v-if="item.text">{{ item.text }}</text>
			</view>
		</view>
	</view>
</template>

<script setup>
	import {
		onMounted,
		ref
	} from 'vue';

	const emit = defineEmits(['clickTab'])
	const props = defineProps({
		//默认选中菜单
		defaultSel: {
			type: Number,
			default: 0
		},
		//选中颜色
		hoverColor: {
			type: String,
			default: "#4484f0"
		},
		//默认颜色
		color: {
			type: String,
			default: "#666666"
		},
		//菜单配置
		list: {
			type: Array,
			default: []
		}
	})


	const selIdx = ref(-1)
	onMounted(() => {
		selIdx.value = props.defaultSel;
	})

	const click = (idx) => {
		selIdx.value = idx;
		emit("clickTab", idx)
	}
</script>

<style scoped lang="scss">
	.tabbar-box {
		position: fixed;
		bottom: 0;
		left: 0;
		z-index: 999;
		width: 100%;
		height: 130rpx;
		background-color: #ffffff;
		display: flex;
		align-items: center;
		box-shadow: 0rpx 0rpx 12rpx rgba(0, 0, 0, 0.2);
	}

	.menu-list {
		display: flex;
		justify-content: space-around;
		text-align: center;
		font-size: 28rpx;
		width: 100%;
		align-items: center;

		.item {
			flex: 1;
			display: flex;
			flex-direction: column;
			align-items: center;
			box-sizing: border-box;
			height: 100%;
			font-size: 22rpx;
			//color: #757575;

			image {
				width: 46rpx;
				height: 46rpx;
			}

			.label {
				margin-top: 6rpx;
			}

			.icon-box {
				width: 46rpx;
				height: 46rpx;
				text-align: center;
				display: flex;
			}

		}


	}
</style>
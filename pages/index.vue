<template>
	<view>
		<view v-show="tabBarIdx==0">
			<home />
		</view>
		<view v-show="tabBarIdx==1">
			<find />
		</view>
		<view v-show="tabBarIdx==2">
			<msg />
		</view>
		<view v-show="tabBarIdx==3">
			<my />
		</view>
		<customTabBar :list="tabbarList" :defaultSel="0" @clickTab="clickTab"></customTabBar>
	</view>
</template>

<script>
import customTabBar from "@/components/custom-tabbar/custom-tabbar.vue";
import home from "./home.vue";
import find from "./find.vue";
import msg from "./msg.vue";
import my from "./my.vue";

export default {
	components: {
		customTabBar,
		home,
		find,
		msg,
		my
	},
	
	data() {
		return {
			tabBarIdx: 0,
			tabbarList: [
				{
					"iconPath": "/static/images/tabbar/home.png",
					"selectedIconPath": "/static/images/tabbar/home_.png",
					"text": "首页",
					"role": ["user", "provider"]
				},
				{
					"iconPath": "/static/images/tabbar/find.png",
					"selectedIconPath": "/static/images/tabbar/find_.png",
					"text": "发现",
					"role": ["user"]
				},
				{
					"iconPath": "/static/images/tabbar/msg.png",
					"selectedIconPath": "/static/images/tabbar/msg_.png",
					"text": "消息",
					"role": ["user"]
				},
				{
					"iconPath": "/static/images/tabbar/my.png",
					"selectedIconPath": "/static/images/tabbar/my_.png",
					"text": "我的",
					"role": ["user", "provider"]
				}
			]
		}
	},

	methods: {
		clickTab(idx) {
			this.tabBarIdx = idx;
			console.log(idx);
		}
	},

	onLoad(options) {
		if (options.role === 'user') {
			this.tabbarList = this.tabbarList.filter(item => item.role.includes('user'))
		} else {
			this.tabbarList = this.tabbarList.filter(item => item.role.includes('provider'))
		}
	}
}
</script>

<style scoped lang="scss">

</style>
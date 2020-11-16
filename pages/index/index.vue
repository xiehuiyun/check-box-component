<template>
	<view>
		<xhy-check-box-group @change="setSelect" :selectList="select">
			<xhy-check-box label="box1" value="1" :size="size" color="#0000ff"></xhy-check-box>
			<xhy-check-box label="box2" value="3" :size="size"></xhy-check-box>
		</xhy-check-box-group>
		
		<view>设置chexkbox的大小：</view>
		<input placeholder="请输入" type="number" v-model="size"/>

	</view>
</template>

<script>
	import xhyCheckBox from '@/components/xhy-check-box/xhy-check-box';
	import xhyCheckBoxGroup from '@/components/xhy-check-box/xhy-check-box-group';
	export default {
		components: {
			xhyCheckBox,
			xhyCheckBoxGroup
		},
		data() {
			return {
				select: ['1'],
				size:25
			}
		},
		onLoad() {

		},
		methods: {
			setSelect(e) {
				this.select = e;
			}
		}
	}
</script>

<style>
	view{
		padding: 30upx;
	}
	input{
		border: 1upx solid #EBEBEB;
		margin: 30upx;
		border-radius: 8upx;
		padding: 15upx 30upx;
	}
</style>

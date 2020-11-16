<template>
	<label class="check-box-div" @tap="selfClick">
		<text class="iconfont" :style="'color:'+color+';font-size:'+size+'px;'" :class="{'icon-check_box_px_rounded':isSelect,'icon-checkboxoutlineblank':!isSelect}"></text>
		<text>{{label}}</text>
	</label>
</template>

<script>
	export default {
		name: 'xhyCheckBox',
		/**
		 * 显示的名称 对应的数值  是否选中
		 */
		props: {
			size:{
				type: [Number,String],
				default: 25
			},
			color: {
				type: String,
				default: '#00FF00'
			},
			label: {
				type: String,
				default: ''
			},
			checked: {
				type: Boolean,
				default: false
			},
			value: {
				type: [String, Boolean],
				default: ''
			}
		},
		inject: ['xhyCheckBoxGroup'],
		data() {
			return {
				isSelect: false
			}
		},
		created() {
			this.isSelect = this.checked;
		},
		methods: {
			/**
			 * 当前点击，向上级传递数据
			 */
			selfClick() {
				this.isSelect = !this.isSelect;
				this.xhyCheckBoxGroup.setChildStatus({
					isSelect:this.isSelect,
					value:this.value===''?this.label:this.value
				});
			},
			setRadioStatus(status) {
				this.isSelect = status;
			}
		}
	}
</script>

<style scoped>
	@import url("/static/xhy-check-box/xhy-iconfont.css");

	.check-box-div {
		max-width: 240upx;
		margin-right: 10upx;
		display: inline-flex;
		justify-content: flex-start;
		align-items: center;
	}
</style>

<template>
	<view class="left_center">
		<slot></slot>
	</view>
</template>

<script>
	export default{
		name:'xhyCheckBoxGroup',
		props:{
			selectList:{
				type:Array,
				default (){
					return []
				}
			}
		},
		data() {
			return {
				value: []
			}
		},
		provide(){
			return {
				xhyCheckBoxGroup:this
			}
		},
		mounted() {
			if(this.selectList.length>0){
				let initValue = this.selectList.join(',');
				this.$children.forEach(item=>{
					let value = item.value===''?item.label:item.value;
					if(initValue.indexOf(value)>-1){
						item.setRadioStatus(true);
					}
				});
			}else{
				this.$children.forEach(item=>{
					if(item.isSelect){
						this.value.push(item.value===''?item.label:item.value);
					}
				});
			}
		},
		methods:{
			setChildStatus(item){
				if(item.isSelect){
					this.value.push(item.value);
					this.$emit('change',this.value);
				}else {
					for (let i = 0; i < this.value.length; i++) {
						if(this.value[i] == item.value){
							this.value.splice(i,1);
							this.$emit('change',this.value);
							return;
						}
					}
				}
			}
		}
	}
</script>

<style>
</style>

<template>
	<div>
		<item :item="item"></item>
		<button @click="$store.dispatch('updateData')" class="btn">增加</button><br />
		<button class="btn">{{ item }}</button><br />
		<input :value='msg' @input='updateMsg' class="msg"/>
		<p>{{ msg }}</p>
		<button @click="changeBG" class="btn">改变背景色</button><br />
		<p id="bg">点击按钮会改变背景色</p>
		<button class="btn" @click="lookData">查看列表</button>
	</div>
</template>

<!--<script src="../assets/libs/bootstrap/js/bootstrap.min.js"></script>-->
<script>
	import item from './item';
	import { mapState }  from 'vuex';
	export default {
		data() {
			return {
//				item: this.$store.state.item
			}
		},
		components: {
			item
		},
		computed: {
			...mapState({
				msg: state => state.obj.msg,
				item: state => state.item
			})
			//此做法也可行
//			item() {
//				return this.$store.state.item;
//			}
		},
		methods : {
			updateMsg(e) {
				this.$store.commit('updateMsg',e.target.value);
			},
			changeBG() {
				jQuery("#bg").css("background",'grey').css('color','#fff');
			},
			lookData() {
				this.$router.push('list');
			}
		}
	}
</script>

<style>
	@import '../common/style/main.css';
</style>
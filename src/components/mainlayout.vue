<template>
	<div>
		<item :item="item"></item>
		<button @click="$store.dispatch('updateData')">增加</button><br />
		<button>{{ item }}</button><br />
		<input :value='msg' @input='updateMsg'/>
	</div>
</template>

<script>
	import item from './item';
	export default {
		data() {
			return {
				item: this.$store.state.item
			}
		},
		components: {
			item
		},
//		computed: {
//			msg : {
//				get () {
//					return this.$store.obj.msg;
//				},
//				set (value){
//					this.$store.commit('updateMsg',value);
//				}
//			}
//		},
		methods : {
			counter() {
				this.$store.dispatch('updateData');
			},
			updateMsg(e) {
				this.$store.commit('updateMsg',e.target.value);
			}
		}
	}
</script>

<style>
</style>
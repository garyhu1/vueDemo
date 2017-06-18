<template>
	<div>
		<item :item="item"></item>
		<button @click="$store.dispatch('updateData')" class="btn">增加</button><br />
		<button class="btn">{{ item }}</button><br />
		<input :value='msg' @input='updateMsg' class="msg"/>
		<p @click='toForm' class="pClick">{{ msg }}</p>
		<button @click="changeBG" class="btn">改变背景色</button><br />
		<p id="bg">点击按钮会改变背景色</p>
		<button class="btn" @click="lookData">查看列表</button>
		<br/>
		<button class='btn' @click="getTodo">获取数据</button>
		<div v-for='item in todos'>
		    <p>
			   <span>{{item.title}}</span>
			   <span>{{item.count}}</span>
			</p>
		</div>
	</div>
</template>

<!--<script src="../assets/libs/bootstrap/js/bootstrap.min.js"></script>-->
<script>
	import item from './item';
	import { mapState }  from 'vuex';
    import { getTodoList } from '../api/api';

	export default {
		data() {
			return {
				todos: []
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
			},
			getTodo() {
				this.todos = [{title: "llal",count: 2},{title: "asd",count: 72}]
				getTodoList({}).then(res => {
					const TODOS = res.data.todos;
					this.todos = TODOS;
				});
			},
			toForm() {
				this.$router.push('form');
			}
		}
	}
</script>

<style>
	@import '../common/style/main.css';
</style>
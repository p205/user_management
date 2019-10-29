<template>
  <div class="container">
		<Alert/>
		<h1 class="page-header">用户列表</h1>
    <table class="table">
      <thead>
        <tr>
          <th>编号</th>
          <th>name</th>
          <th>age</th>
          <th>password</th>
          <th>操作</th>
        </tr>
      </thead>
      <tbody>
        <tr class="info" v-for="user in users" v-bind:key="user.id">
          <td>{{user.id}}</td>
          <td>{{user.name}}</td>
          <td>{{user.age}}</td>
          <td>{{user.password}}</td>
          <td>
            <ul class="nav navbar-nav">
              <li>
								<router-link to="/useradd" class="btn btn-default">增</router-link>
								</li>
								<li>
									<router-link to="/userdel" class="btn btn-default">删</router-link>
								</li>
								<li>
								<router-link to="/userupdate" class="btn btn-default">改</router-link>
								</li>
            </ul>
          </td>
        </tr>
      </tbody>
    </table>
    <div id="box">
      <input type="button" @click="fetchUsers()" value="点我异步获取用户数据" />
    </div>
  </div>
</template>
<script>
import Alert from '../Alert'
export default {
  name: "List",
  data() {
    return {
      users: []
    };
  },
  methods: {
    fetchUsers() {
      this.$http.get("http://127.0.0.1:3000/users").then(
        function(res) {
          this.users = res.body;
          // console.log(res.body);
        },
        function() {
          console.log("请求失败");
        }
      );
    }
  },
  created() {
    // 进入页面刷新数据
    this.fetchUsers();
	},
	components:{
		Alert
	}
};
</script>
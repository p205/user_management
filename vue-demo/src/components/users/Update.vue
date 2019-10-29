<template>
  <div class="add container">
      <h1 class="page-header">修改用户</h1>
    <div class="row clearfix">
      <div class="col-md-12 column">
        <form role="form" v-on:submit="updateUser">
          <div class="form-group">
            <label for="userid">id</label>
            <input type="text" class="form-control" id="userid" v-model="user.id"/>
          </div>
          <div class="form-group">
            <label for="username">name</label>
            <input type="text" class="form-control" placeholder="username" id="username" v-model="user.name"/>
          </div>
          <div class="form-group">
            <label for="userage">age</label>
            <input type="text" class="form-control" placeholder="age" id="userage" v-model="user.age"/>
          </div>
          <div class="form-group">
            <label for="userpassword">password</label>
            <input type="password" class="form-control" placeholder="password" id="userpassword" v-model="user.password"/>
          </div>
          <!-- form制定submit -->
          <button type="submit" class="btn btn-default">Submit</button>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: "useradd",
    // 这里初始化对象不能少，否则一片红
    data(){
        return{
            user:{}
        }
    },
    methods:{
        // 传入e, 阻止默认事件
        updateUser(e){
            // console.log(123);
            this.$http.put("http://localhost:3000/users", this.user).then(
                function(res){
                    console.log(res);
                },
                function(){
                    console.log("添加用户失败");
                }
            )
            e.preventDefault();
        },
        fetchUser(){
          this.$http.get("http://localhost:3000/users/1").then(
            function(res) {
              console.log(res)
              // this.user = res.body;
            },
            function(){
              console.log("根据id获取用户失败")
            }
          )
        }
    },
    created(){
      // 修改进入页面就填充数据
    }
}
</script>
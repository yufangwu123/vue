<template>
  <div id="app">
    {{ message }}
    <ol>
      <!--
            现在我们为每个 todo-item 提供 todo 对象
            todo 对象是变量，即其内容可以是动态的。
            我们也需要为每个组件提供一个“key”，稍后再
            作详细解释。
          -->
      <button v-on:click="getUsers">query</button>
      <todo-item v-for="item in users" :key ="item.userName" :userName="item.userName" :passWord ="item.passWord"></todo-item>
    </ol>
  </div>
</template>
<script>
import todoItem from "./component/todoItem";
export default {
  name: "app",
  components: {
    todoItem,
  },
  data() {
    return {
      message: "helloword",
      users: [],
    };
  },
  methods : {
            getUsers :function(event){
                 let _this = this;
                let formData = new FormData();
                formData.append("pages", 1);
                fetch('http://localhost:8081/user/findByPage', {
                    method: 'post',
                    body: formData,
                    headers: new Headers({
                        'Accept': 'application/json' // 通过头指定，获取的数据类型是JSON
                    })
                }).then(function (response) {
                    return response.json()
                }).then(function (data) {
                    console.log(data);
                    _this.users = data;
                }).catch(function (e) {
                    console.log("Oops, error");
                });
            }
            }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1,
h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>

<template>
  <li>{{userName}},{{passWord}}</li>
</template>
<script>
export default {
  props: {
    userName:String,
    passWord:String
  },
  
  //   methods: {
  //     getUsers: function (event) {
  //       let _this = this;
  //       let formData = new FormData();
  //       formData.append("pages", 1);
  //       fetch("http://localhost:8081/user/findByPage", {
  //         method: "post",
  //         body: formData,
  //         headers: new Headers({
  //           Accept: "application/json", // 通过头指定，获取的数据类型是JSON
  //         }),
  //       })
  //         .then(function (response) {
  //           return response.json();
  //         })
  //         .then(function (data) {
  //           console.log(data);
  //           _this.users = data;
  //         })
  //         .catch(function (e) {
  //           console.log("Oops, error");
  //         });
  //     }
  //   }
};
</script>
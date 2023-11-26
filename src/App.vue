<template>
  <div class="main">

     <form class="form" @submit.prevent>
       <h4>Add Task</h4>
       <input v-bind:value="title" type="text" @input="title = $event.target.value" placeholder="Write any data">
       <button @click="addPost">Add New Post</button>
     </form>

     <div class="tasks">
       <ul>
          <li v-for="(post,index) in posts" :key="index">
            <div>{{ post.title }}</div>
            <button @click="dropPost(index)">Delete</button>
          </li>
       </ul>
     </div>
   </div>
</template>

<script>
   export default{
     data(){
        return {
          posts:[ 
            {title:'daniyal'}
          ],
           title:''
        }
     },
     methods:{
      addPost(event){
        const newPost = {
          title: this.title
        }
        if(this.title.trim()!==''){
        this.posts.push(newPost);
        this.title = '';
        }
      },
      dropPost(index){
            this.posts.splice(index,1);
      }
     }
   }
</script>

<style>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
#app {
  background-color: teal;
      text-align: center;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      height: 100vh;
      padding: auto;
}
.main{
  width: 700px;
}
.form h4{
  font-size: 25px;
  color: azure;
  margin-bottom: 15px;
}
.form input{
  padding: 10px;
  outline: none;
  border: none;
  border-radius: 10px;
  margin-right: 10px;
  width: 500px;
}
.form button{
  padding: 10px;
  outline: none;
  border: none;
  border-radius: 10px;
  color: aliceblue;
  background-color:hotpink ;
}
.tasks ul{
  text-decoration: none;
  list-style: none;
}
.tasks li{
  background-color: aliceblue;
  margin: 15px 0;
  padding: 15px;
  border-radius: 15px;
  display: flex;
  justify-content: space-between;
  font-size: 20px;
  word-wrap:break-word;
}
.tasks button{
  background-color: hotpink;
  color: aliceblue;
  padding: 5px 8px;
  outline: none;
  border: none;
  border-radius: 3px;
}
</style>

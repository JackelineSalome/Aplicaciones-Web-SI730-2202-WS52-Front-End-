<template>

  <Button class="p-button-outlined"><router-link to="/comment" class="back">Back</router-link></Button>
    <form>
      <div class="field grid">
        <label for="body" class="col-1 mb-2" >Body</label>
        <InputText id="body" v-model="body" />
      </div>

      <div class="field grid">
        <label for="postId" class="col-1 mb-2"  >Post</label>
        <pv-dropdown  v-model="seletedPost"  :options="posts" optionLabel="title" placeholder="Select a post" />
      </div>

      <Button @click="save"  >Save</Button>
    </form>

</template>

<script>
import { CommentsServices } from "@/services/coments-services";
import { PostsServices } from "@/services/post-services";
export default {
  name: "comment.new",
  data(){
    return{
      body: "",
      seletedPost: "",
      posts: null
    }
  },
  methods: {
    save: function(){
      debugger
      console.log("body",this.body)
      console.log("id",this.seletedPost.id)
      new CommentsServices().postComment(this.body,this.seletedPost.id ).then(
          //console.log("commentario correctamente grabado")
          //Retornar
          this.$router.push('/comment')
      )
    }
  },
  created() {
    new PostsServices().getPots().then(response => {
      this.posts = response.data
    } )
  }
};
</script>

<style scoped>
.back{
  color: #0b7ad1;
  cursor: pointer;
  text-decoration: none;
  cursor: pointer;
  font-family: "Arial Black";
  font-size: 15px;
}
</style>
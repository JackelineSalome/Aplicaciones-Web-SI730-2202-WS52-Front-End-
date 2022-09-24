<template>

  <Button class="p-button-outlined"><router-link class="newcoment" to="/newcomment">New comment</router-link></Button>
  <pv-dataTable :value="comments">

    <pv-column field="id" header="Id"></pv-column>
    <pv-column field="body" header="Body"></pv-column>
    <pv-column field="postId" header="Post Id">

    </pv-column>
    <pv-column field="eliminar" header="Delete">

      <template #body="slotProps">
        <Button @click="deleteComment(slotProps.data.id)"   >Eliminar </Button>
      </template>

    </pv-column>
  </pv-dataTable>
</template>

<script>
import { CommentsServices } from "@/services/coments-services";
export default {
  name: "Comment",
  data(){
    return {
      comments: null
    }
  },
  methods:{
    deleteComment: function(id){
      //console.log("eliminando comment " + id)
      new CommentsServices().deleteComment(id).then(response)
    }
  },
  created() {
    new CommentsServices().getComments().then(response =>  {
      this.comments = response.data
    })
  }
};
</script>

<style scoped>
.newcoment{
  color: #0b7ad1;
  cursor: pointer;
  text-decoration: none;
  cursor: pointer;
  font-family: "Arial Black";
  font-size: 15px;
}
</style>
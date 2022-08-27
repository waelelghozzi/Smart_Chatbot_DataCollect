

<template>
  <div class="row">
    <div class="container_d">
    <img src="/images/chatbot/Women Power - Avatar.png" alt="" class="botpic">

      <div class="container_d_2">
      <div 
          class="deliv"
          v-for="(del, id, index) in this.sen[v1]"
          :key="index" >
          {{del}}
      </div>
</div>
</div>

    <div class="container_r">
      <div class="messages_r">
        <div
          class="clickr"
          v-on:click="next(id)"
          v-for="(msg, id, index) in this.sen[v2]"
          :key="index">

          {{ msg }}

        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "row",

  props: {
    sen: {
      type: Array,
      required: true,
    },

    v1: Number,
    v2: Number,
  
    keyr:Number,

    collectedData:{
          type: Object,
      required: true,
    }
  },

  data() {
    return {};
  },

  methods: {
    next(id) {
      this.$emit("add", { d: id, i: this.keyr });
      
    },
  },
};
</script>






<style>

.container_d {
  width: 100%;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  color: black;
  margin-top: 2px;
  margin-bottom: 2px;
}
.deliv { 
     max-width: max-content;
 

  background-color: #f0eeee;
  border-radius: 25px;
  padding: 10px;
  margin: 4px;
  
  user-select: none;
}

.container_r {
  width: 100%;
  display: flex;
 color: black;
 flex-direction: column;
}
.messages_r {
  width: 100%;
  display: flex;
  flex-direction: column;
  align-self: flex-end;
  
}

.clickr {
     
  min-width: max-content; ;
 background-color: #bbbbbbde;
  border-radius: 25px;
  padding: 10px;
  margin-top: 5px;
  margin-bottom: 5px;
  margin-left: 10px;
  margin-right: 10px;
  align-self: flex-end;
  user-select: none;
}
.clickr:hover {
   background-color: #deeafd;
  transition: all 0.2s;
}

.botpic{
    align-self: flex-end;
    height: 45px;
    width: auto;
  margin-left: 10px;
  margin-bottom: 4px;
  
}
.container_d_2{
    display: flex;
    flex-direction: column;
}



</style>



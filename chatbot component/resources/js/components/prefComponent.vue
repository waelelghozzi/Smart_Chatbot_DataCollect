
<template>
  
<div class="singelpref" v-on:click="addtop()">{{v}}</div>

</template>

<script>
export default {
  name: "pref",

  props: {
    v:String,
    s:Number,
    h:Number,
    },
 

  data() {
    return {
        f:0,
        
    };
  },

  methods: {
    addtop(){
      
         if(this.f==0){   
                   document.querySelector('.singelpref:nth-child('+((this.s)+1)+')').style.backgroundColor="#43c7de";
                        document.querySelector('.singelpref:nth-child('+((this.s)+1)+')').style.color="white"
                        document.querySelector('.b2').style.color="#153b61"  
                     this.$emit("topref", this.v);this.f=1;}
             else{
                  document.querySelector('.singelpref:nth-child('+((this.s)+1)+')').style.backgroundColor="#f4f4f4";
                  document.querySelector('.singelpref:nth-child('+((this.s)+1)+')').style.color="black"
                       this.$emit("downref", this.v);this.f=0;}
      
      }
           
         },
};
</script>

<style>

.singelpref{
  font-family: made4;
    border-radius: 25px;
    background-color: #f4f4f4;
    padding: 10px;
    margin: 5px;
    transition: all 0.3s;
    user-select: none;
    cursor: pointer;
    color: black;
}
.singelpref:hover{
    background-color: rgb(218, 216, 216);
}
</style>
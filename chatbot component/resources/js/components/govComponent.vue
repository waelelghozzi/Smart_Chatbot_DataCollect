
  <template>
<div class="singelpref2" v-on:click="addtop()">{{v}}</div>

</template>

<script>
export default {
  name: "gov",

  props: {
    v:String,
    s:Number,
   
    },
 

  data() {
    return {
       
        
    };
  },

  methods: {
    addtop(){
       for(let i=1;i<=24;i++){
        if(i!=this.s+1){
            document.querySelector('.singelpref2:nth-child('+i+')').style.backgroundColor="#f4f4f4";
            document.querySelector('.singelpref2:nth-child('+i+')').style.color="black";
           
        }
        
       }
         document.querySelector('.singelpref2:nth-child('+((this.s)+1)+')').style.backgroundColor="#43c7de";
                       document.querySelector('.singelpref2:nth-child('+((this.s)+1)+')').style.color="white";
                       let el = document.querySelectorAll('.b2');
                         el[1].style.color='#153b61';
                     
                       this.$emit("topref2", this.v);}
   
           
         },
};
</script>

<style>
.singelpref2{
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
.singelpref2:hover{
   background-color: rgb(218, 216, 216);
}
</style>

<template>

<div class="contain">
<img src="/images/chatbot/Buddy_no_connection_transparent_by_Icons8.gif" class="chatcat1" alt=""
 v-on:click="pre_prebegin()" :style="{ display: status4 }">

<div class="blur" :style="{ display: status9 }" @click="cl()"></div>


  <div class="wrapper" :style="{ display: status8 }">

    <img src="/images/chatbot/Buddy_done_transparent_by_Icons8.gif" class="chatcat2" alt="" v-on:click="prebegin()" :style="{ display: status3 }"
     @mouseover="red()" @mouseout="normal()">
    <p class="pmsg" :style="{ display: status3 }">stranger ! you clicked on me.. 
    i see you're curious, i'll set you up.. <span class="click"> click again.</span></p>
    <h1 class="msg" :style="{ display: status1 }">
  <span>my</span>
  <span>name</span>
  <span>is</span>
  <span>chatcat</span>
  <span>!</span>
  <span>and</span>
  <span>i am</span>
  <span>soo</span>
  <span>excited</span>
  <span>to</span>
  <span>know</span>
  <span>more</span>
  <span>about</span>
  <span>you</span>
  <br>
  <span v-on:click="begin()">lets begin!</span>
    </h1>

<div class="pa">
    <rw v-for="m in valuesins"
      :key="m.id"
      :keyr="m.id"
       class="row"
      :sen="sen"
      :v1="m.v1"
      :v2="m.v2"
      :collectedData="collectedData"
      v-on:add="secondFunction($event)"
      :style="{ display: status2 }"/> 
      
    <div class="inputsection">
        <input type="text" class="in" value="" @keyup.enter="returnTomsg(0)" @focus="focus(0)" @blur="blur(0)">
        <button @click="returnTomsg(0)" class="inb" >➜</button>
    </div>
      <div class="mail">
        <input type="mail" class="in2" value="" @keyup.enter="returnTomsg(1)" @focus="focus(1)" @blur="blur(1)">
        <button @click="returnTomsg(1)" class="inb" >➜</button>
    </div>
    <div class="photo">
        <input type="file" name="avatar_file" 
         class="inf"  @keyup.enter="returnTomsg(2)" @focus="focus(1)" @blur="blur(1)">
        <button @click="returnTomsg(2)" class="inb" >➜</button>
    </div> 
    <div class="container_d" :style="{ display: special }">

    <img src="/images/chatbot/Women Power - Avatar.png" alt="" class="botpic">
    <div class="btn-shine" >...</div>

    </div>
</div>
    <div class="c1" :style="{ display:status5 }">
     
       <div class="prefc">
          <prf v-for="(p,index) in preferances"
           :key="p.id"
           :v="p" 
           :s="index"
           class="pref"
           v-on:topref="addtoref2($event)"
           v-on:downref="takedownp($event)"/>
      </div>
      <div class="btnc">
        <button @click="listtomsg()" class="b2">save</button>
      </div></div>
    <div class="c1" :style="{ display:status7 }">
       
      <div class="prefc">
          <gov v-for="(j,index2) in govs"
           :key="j.id" 
           :v="j" 
           
           :s="index2"
           class="pref"
           v-on:topref2="addgov($event)"
           />
      </div>
      <div class="btnc">
        <button @click="listtomsg()" class="b2">save</button>
      </div></div>
    <div class="date" :style="{ display:status6 }">
            <div class="d1"> 
              <p></p>
                 <input type="date" class="ind" @click="inis()">

             </div >
     
             <div class="btnc">
              <button @click="datetomsg()" class="bd2">save</button>
             </div> 
     </div></div>
 </div>
</template>




<script>
import RowComponent from "./rowComponent.vue";
import PerfComponent from "./prefComponent.vue";
import GovComponent from "./govComponent.vue";
//v-on:add="nextRows($event)"


export default {
  name: "chatbot",
  components: {
    rw: RowComponent,
    prf:PerfComponent,
    gov:GovComponent
  },
  
  computed: {
    sample_v() {
      return {
        v1: this.valuesins[this.j].v1 + 2,
        v2: this.valuesins[this.j].v2 + 2,
        id:this.j+1
      };
    },

r2(){
  if(this.collectedData.name===""){ return "je l'ecrit pour toi";}
  else{return this.collectedData.name}},
r6(){
  if(this.collectedData.lastname==""){ return "je l'ecrit aussi";}
  else{return this.collectedData.lastname}},
r10(){
  if(this.collectedData.birthdate==""){ return "bien sure !";}
  else{return this.collectedData.birthdate}}},



  data() {
    return {

preferances:["charismatique","créatif","dandy","détente","économe","entrepreneur","extraverti","étudiant","facile à vivre","flemmard","fort tempéramment","fun","galérien","garde-tout","généreux","génie","grand coeur","hyperactif","introverti","joyeux","leader","ouvert d'esprit","perfectionniste","pipelette","proactif","professionnel","romantique","sociable","solitaire","spontané","à l'arrache ","APL","aventurier ","bonvivant ","bordélique ","organisé ","célibataire ","en couple","Clubber","Couche-tard","Ecolo","Fêtard","Fumeur","j'ai un animal","j'ai un chat ","j'ai un chien","lêve tôt","main verte ","Maniaque ","Mr/Mme propre*","Non Fumeur ","permis de conduire ","pilier de bar ","ponctuel","pro du canap","super busy","super star","sain ","tolere le tabac","toujours en retard "],
//preferances:[],
govs:["Ariana","Bèja","Ben Arous","Bizerte","Gabès","Gafsa","Jendouba","Kairouan","Kasserine","Kébili","La Manouba","Le Kef","Mahdia","Medenine","Monastir","Nabeul","Sfax","Sidi Bouzid","Siliana","Sousse","Tataouine","Tozeur","Tunis","Zaghouan"],
 collectedData:{
        name:'',
        lastname:'',
        birthdate:'',
        preferances_chosen:[],
        account_type:'',
        governorat:'',
        moving:'null',
        renting:'null',
        findate:'',
        mail:'',
        photo:''
      },
sen: [
        {d1:"hey, bievenue chez Coloc'Qui 😎",d2:"Je suis chatcat m'envoie pour t'aider à la chasse de trésor ",d3:"should we start ?"},
        {r1: "lets go ! 🚀"},
        
        {d3:"faisons connaissance !",d4:"quel est ton prénom ?"},
        {r2:"je l'ecrit pour toi"},
        
        {d4:"es- tu sûr  ?"},
        {r3: "oui , je suis sûr ", r4: "non , j'ai fait une faute" },
        
        {d5:"alors, dis moi comment tu t'appelles vraiment ?"},
        {r5:"ok je le correct"},

        {d6:"quel est ton nom de famille ?",d7:" promis ça reste entre nous 😆"},
        {r6:"je l'ecrit aussi"},

        {d8:"ravi de te rencontrer laisse-moi mettre un visage sur ton prénom 😏"},
        {r7:"non on se connait pas enocre assez ",r8:"uploader une photo"},
        
        {d9:"pas de souci tu peux faire ça plus tard !"},
        {r9:"ok, en passe à la question suivante"},

        {d10:"peux tu me donner ta date de naissance ? moi c'est le 23 mars 2022 !"},
        {r10:"bien sure 😇"},

        {d11:"ok super séléctionne les mots clé qui te correspond le plus"},
        {r11:"je passe a la liste des mots"},

        {d11:"tu es un seeker ou provider ? 🏡"},
        {r12:"seeker",r13:"provider"},

//question pour seekers//20
        {d12:"dans quelle ville recherches tu des colocs/ camarades ?"},
        {r14:"je déménage vers.."},
//question pour providers         
        {d13:"dans quelle ville habites tu actuellement avec des colocs/ camarades ?"},
        {r15:"j'habite a.."},
//question pour seekers//     
        {d14:"super j'adore cette ville ! 👌🏼",d15:"quand penses - tu démenager ? "},
        {r16:"je donne la date"},
//question pour providers     26/27
        {d16:"super j'adore cette ville ! 👌🏼",d17:"quand sera t 'elle disponible la chambre / logement ?"},
        {r17:"je donne la date"},
        
        {d18:"donner mois la date du fin contracts"},
        {r18:"ok je l'ecrit"},

        {d19:"finallement ! saisi ton mail"},
        {r19:"ok je passe le mail"},
        
       // {d20:"tu a deja un compte",d20:"tu peux ajouter ou modifier tes informations à tout moment dans ton profil",d21:"félicitations ! tu es désormais un'coloc"},
       // {r20:"au revoir"},

        {d20:"merci pour ces infos je suis sur le point de vous trouver les meilleurs colocataires"
        ,d20:"n'oublie pas que tu peux ajouter ou modifier tes informations à tout moment dans ton profil"
        ,d21:"NB: il faux verifier ton mail pour avoir la sauvgarde des donnees"
        ,d22:"félicitations ! tu es désormais un'coloc ✨"},
        {r20:"au revoir"},],

      j: 0,
      valuesins: [{ v1: 0, v2: 1, id:0 }],
    ps:null,
    status1:'none',
    status2:'none',
    status3:'none',
    status4:'block',
    status5:'none',
    status6:'none',
    status7:'none',
    num:Number,
    sli1:0,
    dor:0,
    status8:'none',
    status9:'none',
    started:0,
    special:"none"
    };
  },

 

  methods: {

    red(){
      document.querySelector('.click').style.color="#ffa80f";
    },
    normal(){
      
       document.querySelector('.click').style.color="#6a758c";
    },

       pre_prebegin(){
        if(this.started==0){
   this.status3='block';
   this.status8="flex";
   this.status4='none';
   this.status9="block";
   document.querySelector('.blur').style.opacity="1";
   this.started=1;
        }else{
   this.status8="flex";
   this.status4='none';
   this.status9="block";
   document.querySelector('.blur').style.opacity="1";}
   
   },
   cl(){
   this.status8="none";
   this.status4='block';
   this.status9="none";
   document.querySelector('.blur').style.opacity="0";},
      
       prebegin(){
          this.status3='none';
        
          this.status1='block';},

       begin(){
        document.querySelector('.wrapper').style.display="block";
        this.status1='none';
        this.status3='none';
        this.status2='block';
       },

       addtoref2(v){
this.collectedData.preferances_chosen.push(v);
       },
       takedownp(v){
this.collectedData.preferances_chosen.splice(this.collectedData.preferances_chosen.indexOf(v),1);
       },


   firstFunction(v) {
      return new Promise((resolve, reject) => {
          let y = 0
          setTimeout(() => {for (let i=0; i<10; i++) {y++}resolve(y);}, 2000)})
          
          },

    async  secondFunction(v) { 
       if(isNaN(v)){
        if((v.d!=="r2")&&(v.d!=="r5")&&(v.d!=="r6")&&(v.d!=="r10")&&
          (v.d!=="r11")&&(v.d!=="r14")&&(v.d!=="r15")&&(v.d!=="r16")&&
          (v.d!=="r17")&&(v.d!=="r18")&&(v.d!=="r19")){
               //document.querySelector('.wrapper').scroll({top:document.querySelector('.pa').scrollHeight,behavior:"smooth"})
              document.querySelector('.wrapper').scrollTo(0, document.querySelector(".pa").scrollHeight);
          this.special="flex";
          const result = await this.firstFunction(v)}this.nextRows(v);}
          else{
            if(v==1){ 
                
              this.special="flex";
              const result = await this.firstFunction(v);this.special="none";
              this.j++;this.valuesins.push(this.sample_v);
              //document.querySelector('.wrapper').scroll({top:document.querySelector('.pa').scrollHeight,behavior:"smooth"})
              document.querySelector('.wrapper').scrollTo(0, document.querySelector(".pa").scrollHeight);
              }
              else{
                    
              this.special="flex";
              const result = await this.firstFunction(v);this.special="none";
              this.valuesins.push(this.sample_v);
              //document.querySelector('.wrapper').scroll({top:document.querySelector('.pa').scrollHeight,behavior:"smooth"})
              document.querySelector('.wrapper').scrollTo(0, document.querySelector(".pa").scrollHeight);
              }}
       },

    nextRows(ob){ 
      this.special="none";  
      if ((ob.i === this.valuesins.length - 1) && (this.valuesins[ob.i].v2 <= this.sen.length -1 )){
          
        if(ob.d==="r1"){
            this.valuesins.push(this.sample_v);
                this.j++;}   

         else if(ob.d==="r2"){
            this.ecrirenom(2);}  
         else if(ob.d==="r3"){  
          this.sen.splice (6, 2 )
          this.sli1++;
          this.j++;
          this.valuesins.push(this.sample_v);
          this.savename(2);}
         else if(ob.d==="r4"){
          this.j++;
          this.valuesins.push(this.sample_v);}
         else if(ob.d==="r5"){
          this.j++;
          this.ecrirenom(2);}
         else if(ob.d==="r6"){
          this.j++
          this.ecrirenom(6);}
         else if(ob.d==="r7"){
          this.j++;
          this.valuesins.push(this.sample_v);}
           else if(ob.d==="r8"){
               if(this.sli1==1){
              this.sen.splice (10, 2 )
            }else{
              this.sen.splice (12, 2 )
            } 
            this.sli1++
            this.j++;
            this.uphoto();
           //this.valuesins.push(this.sample_v);
           }
           else if(ob.d==="r9"){
          this.j++;
          this.valuesins.push(this.sample_v);}
           else if(ob.d==="r10"){
             this.showdate(1);
         }      
           else if(ob.d==="r11"){
            this.showlist()
           }
             else if(ob.d==="r13"){
              
                if(this.sli1==2){
                   this.sen.splice (16, 2 );
                   this.sen.splice (18, 2 );
                    this.sli1++
                  
                }
                else if(this.sli1==1){
                   this.sen.splice (18, 2 );
                   this.sen.splice (20, 2 );
                     this.sli1++
                }
                else if(this.sli1==0){
                   this.sen.splice (20, 2 );
                   this.sen.splice (22, 2 );
                   this.sli1++
                }
                 this.collectedData.account_type="provider";
                 this.ps=1;
                 this.j++;
          this.valuesins.push(this.sample_v);
           }
           else if(ob.d==="r12"){
                 
                if(this.sli1==2){
                   this.sen.splice (18, 2 );
                   this.sen.splice (20, 2 );
                    this.sli1++
                }
                else if(this.sli1==1){
                   this.sen.splice (20, 2 );
                   this.sen.splice (22, 2 );
                    this.sli1++
                }
                else if(this.sli1==0){
                   this.sen.splice (22, 2 );
                   this.sen.splice (24, 2 );
                    this.sli1++
                }
                 this.collectedData.account_type="seeker";
                  this.ps=0;
                 this.j++;
          this.valuesins.push(this.sample_v);}

            else if((ob.d==="r14")||(ob.d==="r15")){
              this.status7="flex";
              this.status2="none";} 

            else if((ob.d==="r16")||(ob.d==="r17")){
                   if(ob.d==="r16"){this.dor=1;this.showdate(2);}
                               else{this.dor=2;this.showdate(3);}} 

            else if(ob.d==="r18")
            {this.dor=3;this.showdate(4);}
            else if(ob.d==="r19")
            {
              this.j++
              this.ecrirenom(9);
            }

                  else if(ob.d==="r20"){
      
                let formData = new FormData();
                
        formData.append('avatar', this.collectedData.photo);
                formData.append('name', this.collectedData.name);
                formData.append('lastname', this.collectedData.lastname);
                formData.append('birthdate', this.collectedData.birthdate);
                formData.append('account_type', this.collectedData.account_type); 
                formData.append('governorat', this.collectedData.governorat);
                formData.append('moving', this.collectedData.moving);
                formData.append('renting', this.collectedData.renting);
                formData.append('moving', this.collectedData.moving);
                formData.append('findate', this.collectedData.findate);
                formData.append('mail', this.collectedData.mail);
                formData.append('user', JSON.stringify(this.user));
                this.status8="none";
                this.status4="none";
                this.status9="none";console.log(this.collectedData)}
                document.querySelector('.wrapper').scroll({top:50000,behavior:"smooth"})}},


focus(v){
  if(v==0){

    if((document.querySelector('.in').value=="saisi ton nom")||
       (document.querySelector('.in').value=="saisi ton nom de famille")||
       (document.querySelector('.in').value=="saisi un contenu valide..")){
  document.querySelector('.in').value="";}

  document.querySelector('.in').style.color="black";
  document.querySelector('.in').style.border="solid 2px grey";}
  else{

     if((document.querySelector('.in2').value=="saisi ton mail")||
        (document.querySelector('.in2').value=="saisi un contenu valide..")){
         document.querySelector('.in2').value="";}    

      document.querySelector('.in2').style.color="black";
      document.querySelector('.in2').style.border="solid 2px grey";}},



    blur(v){
    if(v==0){

          if((document.querySelector('.in').value=="")){
                 if(this.num==2){
                      document.querySelector('.in').value="saisi ton nom";
                      document.querySelector('.in').style.border="solid 2px #585a5e42";
                    
                      }else{
                      document.querySelector('.in').value="saisi ton nom de famille";
                      document.querySelector('.in').style.border="solid 2px #585a5e42";
                  }}else{
                    if(this.num==2){document.querySelector('.in').style.border="solid 2px #585a5e42";
                  }else{ document.querySelector('.in').style.border="solid 2px #585a5e42";}}
    }else{
    if((document.querySelector('.in2').value=="")){
      document.querySelector('.in2').value="saisi ton mail";
      document.querySelector('.in2').style.border="solid 2px #585a5e42";}
      else{
         document.querySelector('.in2').style.border="solid 2px #585a5e42";
      }
      
}},

    ecrirenom(num){
      this.num=num;
      if(num==2){document.querySelector('.in').value="saisi ton nom";document.querySelector('.inputsection').style.display="flex";}
      else if(num==6){document.querySelector('.in').value="saisi ton nom de famille";document.querySelector('.inputsection').style.display="flex";}
      else{document.querySelector('.mail').style.display="flex";document.querySelector('.in2').value="saisi ton mail";}},

    uphoto(){
      document.querySelector('.photo').style.display="flex";
    },
    
    returnTomsg(v){ 
    
      if(v==0){ let e=document.querySelector('.in').value;
       
        if((e!="saisi ton nom")&&
        (e!="saisi ton nom de famille")&&
        (e!="saisi un contenu valide..")&&
        (e.length<=255)&&(this.verif(e))){
        this.secondFunction(2);
        
        this.status2="block";document.querySelector('.inputsection').style.display="none";
       //
        
         
           if(this.num==2)     {this.savename(2)}
           else if(this.num==6){this.savename(6)}
     }else{
      document.querySelector('.in').style.color ="red";
      document.querySelector('.in').style.border="solid 2px red";
      document.querySelector('.in').value="saisi un contenu valide..";
     }}

     else if(v==1){ 
      let e=document.querySelector('.in2').value;
      //on cherche isi si le mail deja existe ou non 

      //si oui
     // if(ne existe pas){this.sen.slice(this.sen.length-5, 2 )}

      if((e!="saisi ton mail")&&
      (e!="saisi un contenu valide..")&&(e.indexOf('@')!=-1)&&
      (e.indexOf('@')!=e.length)&&(e.indexOf('@')!=0)&&
      (e.indexOf('.')!=-1)&&(e.indexOf('.')!=e.length)&&
      (e.indexOf('.')!=0)&&
      (e.indexOf('.')>e.indexOf('@'))&&
      (e.indexOf('.')!==e.indexOf('@')+1)){
        this.valuesins.push(this.sample_v);
        this.status2="block";document.querySelector('.mail').style.display="none";
      //
        this.savename(9);}
        else{
      document.querySelector('.in2').style.color ="red";
      document.querySelector('.in2').style.border="solid 2px red";
      document.querySelector('.in2').value="saisi un contenu valide..";}
      //si non 
      //else{ this.sen.splice (this.sen.length-3, 2 );}
      }
      else{
       // console.log(document.querySelector('.inf').value)

        if(document.querySelector('.inf').value===""){
         
         document.querySelector('.inf').style.color ="red";
      document.querySelector('.inf').style.border="solid 2px red";
        
        }else{
         this.status2="block";
         document.querySelector('.photo').style.display="none";
         this.secondFunction(2)
       //
         this.savename(12)
        }}
        document.querySelector('.wrapper').scroll({top:document.querySelector('.pa').scrollHeight+1000,behavior:"smooth"})},
    
    verif(e){
      var stringArray = new Array('A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S'
      ,'T','U','V','W','X','Y','Z','a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p'
      ,'q','r','s','t','u','v','w','x','y','z',' ');
        for(let i of e){
            if(stringArray.indexOf(i.toUpperCase())==-1){
              return false;
            }
              }
              return true;
    },


    savename(v){
      if (v==2){this.collectedData.name=document.querySelector('.in').value;
      this.sen[3].r2=this.collectedData.name;}
      else if(v==6){this.collectedData.lastname=document.querySelector('.in').value;
      this.sen[9-this.sli1*2].r6=this.collectedData.lastname;}
      else if(v==9){this.collectedData.mail=document.querySelector('.in2').value;this.sen[31-((this.sli1*2)+2)].r19=this.collectedData.mail;}
      
      else{
        this.collectedData.photo=document.querySelector('.inf').value;
        //console.log(this.collectedData.photo)
      }},

    showlist(){
           this.status5="flex";
           this.status2="none";},

           listtomsg(){
           
              if(this.status7=="flex"){
                if(this.collectedData.governorat!==''){
                          this.status7="none";
                          this.status2="block";
                          this.secondFunction(1);  
                          
                          document.querySelector('.b2').style.color='#153b61';
                      
                        }else{
                        let el = document.querySelectorAll('.b2');
                         el[1].style.color='red';
                        }
              }else if(this.status5=="flex"){
                          if(this.collectedData.preferances_chosen.length!==0){
                            this.status5="none";
                            this.status2="block";
                            this.secondFunction(1);
                            
                             document.querySelector('.b2').style.color='#153b61';
                        
                          }else{
                             document.querySelector('.b2').style.color='red';
                          }}},
           
           
           
           showdate (v){ 
             if(v==1){
              document.querySelector('.d1 p').innerHTML="veuillez saisir votre date de naissance";
             }else if(v==2){
              document.querySelector('.d1 p').innerHTML="veuillez saisir votre date de demenagement ";
             }else if(v==3){
              document.querySelector('.d1 p').innerHTML="veuillez saisir votre date de disponiblité de la chambre"; 
             }else if(v==4){
              document.querySelector('.d1 p').innerHTML="veuillez saisir votre date du fin peride"; 
             }
             document.querySelector('.ind').value="";
             this.status2="none";this.status6="flex";},


           datetomsg(){
            var today = new Date();
            var year = today.getFullYear();
            var day =today.getDay();
            var month =today.getMonth();
            let symbol =document.querySelector('.bd2');
             if(this.dor==0){
              
                  if(((parseInt(year,10))-(parseInt(document.querySelector('.ind').value.substring(0, 4),10)))>=18){
                    this.collectedData.birthdate=document.querySelector('.ind').value;
                    this.sen[15-this.sli1*2].r10=this.collectedData.birthdate;
document.querySelector('.wrapper').scroll({top:50000,behavior:"smooth"})
                    this.status2="block";
                    this.status6="none";
                    this.secondFunction(1);
                    symbol.style.color="#153b61";
                      
                       }else{ 
                       symbol.style.color='red';
               
                      }}

                   else if(this.dor==1){

                     if((parseInt(document.querySelector('.ind').value.substring(0, 4),10)>=(parseInt(year,10)))&&
                     (parseInt(document.querySelector('.ind').value.substring(5,2),10)>=(parseInt(month,10)))&&
                     (parseInt(document.querySelector('.ind').value.substring(8, 2),10)>=(parseInt(day,10)))){

                      this.collectedData.moving=document.querySelector('.ind').value;   
                        this.sen[25-((this.sli1*2))].r16=this.collectedData.moving; //console.log(25-((this.sli1*2))+" 1")     
    document.querySelector('.wrapper').scroll({top:50000,behavior:"smooth"})
                      this.status2="block";
                      this.status6="none";
                      this.secondFunction(1);
                      symbol.style.color="#153b61";}
                      else{
                      symbol.style.color="red";
                      }
                   }else if(this.dor==2){
                     if((parseInt(document.querySelector('.ind').value.substring(0, 4),10)>=(parseInt(year,10)))&&
                     (parseInt(document.querySelector('.ind').value.substring(5,2),10)>=(parseInt(month,10)))&&
                     (parseInt(document.querySelector('.ind').value.substring(8, 2),10)>=(parseInt(day,10)))){

                      this.collectedData.renting=document.querySelector('.ind').value;
                        this.sen[27-((this.sli1*2)+2)].r17=this.collectedData.renting; //console.log(27-((this.sli1*2)+2)+" 2")
    document.querySelector('.wrapper').scroll({top:50000,behavior:"smooth"})
                      this.status2="block";
                      this.status6="none";
                      this.secondFunction(1);
                      symbol.style.color="#153b61";}
                      else{
                       symbol.style.color="red";
                      }
                   }else if(this.dor==3){
                    const d1 = new Date(document.querySelector('.ind').value);
                    const d2 = new Date(this.collectedData.renting);
                    const d3 = new Date(this.collectedData.moving);

                  if(this.collectedData.moving=="null"){
                     if(d1.getTime()>d2.getTime()){
                       this.collectedData.findate=document.querySelector('.ind').value; 
                       this.collectedData.findate=document.querySelector('.ind').value;this.sen[29-((this.sli1*2)+2)].r18=this.collectedData.findate;  
                   
document.querySelector('.wrapper').scroll({top:50000,behavior:"smooth"})             
                       this.status2="block";
                       this.status6="none";
                       this.secondFunction(1);
                       symbol.style.color="#153b61";}
                       else{
                      symbol.style.color="red";
                      }}else{
                        if(d1.getTime()>d3.getTime()){

                      this.collectedData.findate=document.querySelector('.ind').value;this.sen[29-((this.sli1*2)+2)].r18=this.collectedData.findate;
   
document.querySelector('.wrapper').scroll({top:50000,behavior:"smooth"})
                      this.status2="block";
                      this.status6="none";
                      this.secondFunction(1);
                      symbol.style.color="#153b61";}
                    else{
                      symbol.style.color="red";}}}},
                     
                     
                     addgov(v){this.collectedData.governorat=v;
                     if(this.ps==1){
                     this.sen[23-this.sli1*2].r15=this.collectedData.governorat
                     //console.log(23-this.sli1*2)
                     }else{
                     this.sen[21-(this.sli1-1)*2].r14=this.collectedData.governorat
                     //console.log(21-(this.sli1-1)*2)
                     }
                     
                     },
                     inis(){ document.querySelector('.bd2').style.color="#153b61";}
                     
                     
                     },};
</script>




<style>

.pa{
  width: 100%;
  overflow-y: scroll;
  overflow-x: hidden;

}
.pa::-webkit-scrollbar {
  display: none;
}

@font-face {
    font-family: made ;
    src: url(/fonts/otf/Faune-TextItalic.otf);  
}
@font-face {
    font-family: made2 ;
    src: url(/fonts/static/WorkSans-Light.ttf);
}
@font-face {
    font-family: made3 ;
    src: url(/fonts/gilroy/FontsFree-Net-gilory.ttf);
}
@font-face {
    font-family: made4 ;
    src: url(/fonts/gilroy/FontsFree-Net-Gilroy-Light.ttf); 
}
.d1{
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
min-height: 84%;
}
.date{
display: flex;
flex-direction: column;
width: 100%;
height: 100%;
}
.d1 p{
  justify-self: center;
  align-self: center;
 font-family: made3;
margin-bottom: 1em;
 line-height: normal;
font-size: 1.5em;
color: #153b61;
}
.ind{
    padding:1em;
    border-radius: 25px;
    background-color:  #e5efff;
    user-select: none;
    border: none;
    color: rgb(122, 122, 122);
    border-style: none;
    outline: none;
    width: 70%;
    user-select: none;
    cursor: pointer;
}


.b2{
  height: min-content;
  width: min-content;
  padding: 1em;
justify-self: flex-end;
align-self: flex-end;
color: #153b61;
border-radius: 25px;
background-color: #ffd500b9;
       border: none;
    user-select: none;
transition: all 0.3s;
}
.bd2:hover,.b2:hover{background-color: #fae57bb9}

.bd2{
height: min-content;
width: min-content;
padding: 1em;
color: #153b61;
border-radius: 25px;
background-color: #ffd500b9;
border: none;
user-select: none;
transition: all 0.3s;}
.c1{
width: 100%;
display: flex;
flex-direction: column;
height: 100%;
}
.btnc{
  height: 100%;
  display: flex;
  justify-content: flex-end;
  align-content: flex-end;
 padding: 8px;
}
.prefc{
  width: 100%;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  justify-self: center;
}


.click{
    color: #ffa80f;
    transition: all 0.3s;
}

.blur{
  height: 100vh;
  width: 100vw;
  z-index:50;
  position: fixed;
  backdrop-filter: blur(6px);
  transition: all 1s;
}
.wrapper {
  height: 48%;
  width: 24%;
  padding: 8px;
  background-color: #fff9f0da;
  border-radius: 25px;
  overflow-y: scroll;
  display: flex;flex-direction: column;position: fixed;
 z-index: 200;
 margin-top:10% ;
 margin-left:4% ;
 transition: all 0.3s;
 box-shadow: 9px 9px 40px 6px rgba(119, 119, 119, 0.274);
}


@media screen and (max-width: 1200px){
  .wrapper {width: 24%; height: 48%;}}
@media screen and (max-width: 992px){
  .wrapper {width: 30%; height: 48%;}}

@media screen and( max-width: 768px){
  .wrapper {width: 50%;height: 20%;}}

@media screen and (max-width: 600px){
  .wrapper {width: 90%;height:30%;}
  .chatcat1{height: 10%;width: auto;}
  .blur{height: 100vh;width: 100vw;}}



.wrapper p{
    width: 70%;
    text-align: center;
}
.wrapper::-webkit-scrollbar {
  display: none;
}
.pmsg{
   align-self: center;
    justify-self: center;
}
.chatcat2{
    height: 80%;
    width: auto;
    align-self: center;
    justify-self: center;
}
.chatcat1{
height: 20%;
width: auto;
position: fixed;
z-index: 209;
margin-top:10% ;
transition: all 0.3s;}

.chatcat1:hover{
 margin-top: 9%;
}

.inputsection,.mail,.photo{
   
    width: 100%;
    height: 80px;
    background-color: #e5efff;
      border-radius: 25px;
    margin-top: 10px;
    display: none;
    flex-direction: row;
align-items: center;
justify-content: center;}

.in,.in2,.inf{
 background-color: #ffffffb2;
 border: solid 2px #585a5e42;
    font-family: made2;
    height: 60%;
    width: 80%;
    margin: 0.5em;  
      color: #585a5eb4;
 transition: all 0.3s;
   border-radius: 25px;
    user-select: none;
    padding-left: 2.5em;
    overflow: hidden;
}
.inf{
  padding-top: 1.7%;
}
::file-selector-button {
  display: none;
}
.inb{
  margin-left: -0.1em;
    height: 60%;
    width: 10%;
    background-color: #4a4a4b;
       border: none;
    user-select: none;
    overflow: hidden;
    color: #dfe5eb;
    border-radius: 25px;
transition: all 0.3s;
}
.inb:hover{
  padding-left: 8px;
    background-color: #929292;
    color: #353535;
}
* {
  padding: 0;
  margin: 0;
}
.msg {
  font-family: made;
  font-size: 2em;
  width: 80%;
  align-self: center;
  margin-top: auto;
  margin-bottom: auto;
  text-align: center;
  transform: scale(0.94);
  animation: scale 3s forwards cubic-bezier(0.5, 1, 0.89, 1);
}

span {
  display: inline-block;
  opacity: 0;
  filter: blur(4px);
  user-select: none;
}
@keyframes scale {
  100% {
    transform: scale(1);
  }
}
span:nth-child(1) {
  animation: fade-in 0.8s 0.1s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(2) {
  animation: fade-in 0.8s 0.2s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(3) {
  animation: fade-in 0.8s 0.3s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(4) {
  animation: fade-in 0.8s 0.4s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(5) {
  animation: fade-in 0.8s 0.5s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(6) {
  animation: fade-in 0.8s 0.6s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(7) {
  animation: fade-in 0.8s 0.7s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(8) {
  animation: fade-in 0.8s 0.8s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(9) {
  animation: fade-in 0.8s 0.9s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(10) {
  animation: fade-in 0.8s 1s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(11) {
  animation: fade-in 0.8s 1.1s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(12) {
  animation: fade-in 0.8s 1.2s forwards cubic-bezier(0.11, 0, 0.5, 0);
}

span:nth-child(13) {
  animation: fade-in 0.8s 1.3s forwards cubic-bezier(0.11, 0, 0.5, 0);
}
span:nth-child(14) {
  animation: fade-in 0.8s 1.4s forwards cubic-bezier(0.11, 0, 0.5, 0);
}
span:nth-child(15) {
  animation: fade-in 0.8s 1.5s forwards cubic-bezier(0.11, 0, 0.5, 0);
}
span:nth-child(16) {
  animation: fade-in 0.8s 3.5s forwards cubic-bezier(0.11, 0, 0.5, 0);
}



@keyframes fade-in {
  100% {
    opacity: 1;
    filter: blur(0);
  }
}

span:nth-child(16){
    margin-top: 5%;
cursor: pointer;
transition: all 0.3s;
}
span:nth-child(16):hover{
color: brown;
}


.btn-shine{
  font-size: 1.3em;
  max-width: max-content;
  background-color: #f0eeee;
  border-radius: 25px;
  padding: 10px;
  margin: 4px;
  user-select: none;
  animation-name: shine;
  animation-duration: 3s;
  padding-left: 0.5em;
  padding-right: 0.5em;
}

    
@keyframes shine{
   0%{
      color: #3b3b3bda;
   }
  25%{
        color: #f0eeee;
  }
  50%{
  color: #3b3b3bda;
  }
  75%{
        color: #f0eeee;
  }
  100%{
  color: #3b3b3bda;
  }
   
}
 
</style>



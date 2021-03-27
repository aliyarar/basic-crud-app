<template>
  <div>
    <b-container class="bv-example-row">
      <b-row>
        <b-col sm="4">
          <AddRoleModel @fromAddRoleModel="updateCard($event)"/>
        </b-col>
        <b-col sm="8"> 
          <ModelCard v-for="(item,index) in card" 
            :key="index" 
            :index="index" 
            :modelName="item[0]" 
            :modelJob="item[1]" 
            :modelNationality="item[2]"
            :modelBirthDay="item[3]" 
            :modelAbout="item[4]" 
            :modelPic="item[5]" 
            :tags="item[6]" 
             @updateEmitIndex="activeIndex($event)" 
             />
            <UpdateModelCard
             :modelName="card[activeNumber][0]" 
            :modelJob="card[activeNumber][1]" 
            :modelNationality="card[activeNumber][2]"                           
            :modelBirthDay="card[activeNumber][3]" 
            :modelAbout="card[activeNumber][4]" 
            :modelPic="card[activeNumber][5]" 
            :tags="card[activeNumber][6]" 
            v-if="showModel"                           
            @closeModel="updateOkey($event)" 
            @hideUpdateModel="hideUpdateModel()"
            :key="randomKey"
            />
          </b-col>
      </b-row>
    </b-container>
  </div>
</template>


<script>
import globalComponenets from "./components/globalComponents"
export default {
  components: {
    ...globalComponenets
  },
  data(){
    return{
      card:[],
      showModel:false,
      activeNumber: -1,
    }
  },
  methods:{
    updateCard(e){
      this.card.push(e);
      console.log(e);
    },
    activeIndex(e){
      this.showModel = true;
      this.activeNumber = e;
      console.log(e)
    },
    updateOkey(e){
      this.card.splice(this.activeNumber,1,e);
      this.showModel = false;
      this.activeNumber = -1;
    },
  }

};
</script>



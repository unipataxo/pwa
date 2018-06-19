<template>
<div class="dashboard">
    <div class="form-group with-icon-left">
        <div class="input-group">
        <input id="input-icon-left" name="input-icon-left" v-model="search"  v-on:input="search = $event.target.value"> 
        <i class="entypo entypo-search icon-left input-icon"></i> <label for="input-icon-left" class="control-label">Filtrar Aquarios</label><i class="bar"></i></div></div>
   <div class="row">
      <div class="col-sm-12 col-md-6 card" v-for="aquarios in aquariosComFiltro" :key="aquarios.codigo">
         <h4 style="margin-top:10px;">Aquario {{aquarios.codigo}} - <small>Última verificação: 19/06/18 - 12:30</small></h4>
         <ul class="vue-unordered">
            <li><strong>Temperatura:</strong> {{aquarios.temperatura}} ºC</li>
            <li><strong>pH:</strong> {{aquarios.ph}}</li>
            <li><strong>Salinidade:</strong> {{aquarios.salinidade}} ppt</li>
            <li><strong>Volume:</strong> {{aquarios.volume}} L</li>
            <div class="more">
                <li><strong>Transparência:</strong> {{aquarios.transparencia}} cm</li>
                <li><strong>Matéria Orgânica:</strong> {{aquarios.mo}}</li>
                <li><strong>OD:</strong> {{aquarios.od}} mg/L</li>
                <li><strong>Dureza:</strong> {{aquarios.dureza}}</li>
                <li><strong>Amônia:</strong> {{aquarios.amonia}} mg/L</li>
                <li><strong>Nitrito:</strong> {{aquarios.nitrito}}</li>
                <li><strong>H2S:</strong> {{aquarios.h2s}} mg/L</li>
                <li><strong>Silicato:</strong> {{aquarios.silicato}} mg/L</li>
            </div>
            <button class="btn btn-primary btn-micro" @click="moreInfos">
              + Informações
            </button>
         </ul>
      </div>
   </div>
</div>
</template>

<script>
  import $ from 'jquery'

  import DashboardInfoWidgets from './DashboardInfoWidgets'
  import UsersMembersTab from './users-and-members-tab/UsersMembersTab.vue'
  import SetupProfileTab from './setup-profile-tab/SetupProfileTab.vue'
  import FeaturesTab from './features-tab/FeaturesTab.vue'
  import DataVisualisationTab from './data-visualisation-tab/DataVisualisation.vue'
  import DashboardBottomWidgets from './DashboardBottomWidgets.vue'

  export default {
    name: 'aquarios',
  data () {
    return {
      aquarios: [],
      search: '',
    }
  },
    components: {
      DataVisualisationTab,
      DashboardInfoWidgets,
      UsersMembersTab,
      SetupProfileTab,
      FeaturesTab,
      DashboardBottomWidgets
    },
 created(){
    this.$http.get('http://localhost:8080/aquarios').then(response => {

        this.aquarios = response.body;
    
    }, response => {
        // error callback
    });
  },
computed: {

    aquariosComFiltro() {

      if (this.search) {
        let exp = new RegExp(this.search.trim(), 'i');
        return this.aquarios.filter(aquarios => exp.test(aquarios.codigo));
      } else {
        return this.aquarios;
      }

    }
  },
  methods : {
      moreInfos(e){
          $(e.target).prev().slideToggle();
      }
  }
}

</script>
<style lang="scss" scoped>
  @import "../../sass/_variables.scss";
  .card{
      margin-bottom: 20px;
  }
  .more{
      display: none;
  }
</style>

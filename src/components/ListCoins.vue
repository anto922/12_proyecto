<template>

<v-container>
   <v-data-table 
   :headers="headers"
                :items="jData"
                :search="search"
                 show-select
                >
                <template v-slot:top>
      <v-text-field
        v-model="search"
        class="pa-2"
        label="Search"
      ></v-text-field>
    </template>
  </v-data-table> 
</v-container>
</template>

<script>

let url  = "https://api.coincap.io/v2/assets"


export default {
  name: 'ListCoins',
  components: {    
  },
  data(){
    return{
      search: '',
      jData:[],
      headers:[
        { text:'Id', value: 'id' },
        { text:"Simbolo" ,value: 'symbol' },
        { text:"Nombre" , value: 'name' },
        { text:"Precio " , value: 'priceUsd'  ,   align: 'right',}
      ]
    }
  },
  mounted(){
     this.axios.get(url).then((data)=>this.jData=data.data.data);
    
  },
  methods:{


  }
}
</script>

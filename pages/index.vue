<template>
    <div>
        <nav-bar class="mb-10"></nav-bar>
        <v-card>
          <v-card-title>
            <v-col cols="2">
              上市公司基本資料
            </v-col>
            <v-col cols="4">
              <v-text-field v-model="searchQuery" outlined dense hide-details placeholder="查詢"></v-text-field>
            </v-col>
          </v-card-title>
          
          <v-card-text>
            <v-data-table
              :search="searchQuery"
              :headers="basicInfoColumn"
              :items="stockBasicData"
            >
            <template #[`item.Code`]="{ item }">
              <v-spacer class="d-flex justify-center">
                {{ item.Code }}
              </v-spacer>
            </template>
            </v-data-table>
          </v-card-text>
        </v-card>
    </div>
</template>
<script>
import NavBar from '../components/NavBar.vue'

export default {
    components: {
        NavBar
    },
    data() {
      return {
        basicInfoColumn : [
          {
            text:'股票代號',
            align:'center',
            value:'Code'
          },
          {
            text:'股票名稱',
            align:'center',
            value:'Name'
          },
          {
            text:'現金殖利率',
            align:'center',
            value:'DividendYield'
          },
          {
            text:'本益比',
            align:'center',
            value:'PEratio'
          },
          {
            text:'本淨比',
            align:'center',
            value:'PBratio'
          },
        ],
        searchQuery:''
      }
    },
    async asyncData({$axios}) {
      const stockBasicData = await $axios.$get('https://openapi.twse.com.tw/v1/exchangeReport/BWIBBU_d')
      console.log(stockBasicData)
      return {
        stockBasicData
      }
    },
}
</script>
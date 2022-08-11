<template>
  <div id="app">
    <Header :appName="appName"/>
    <div class="max-w-3xl mx-auto" v-if="!loading">
      <div class="p-4 text-center shadow-lg">
          <StatsTitle :title="dateTitle" :date="dataDate" />     
          <StatsSelect :dataCountries="dataCountries" :resetButton="resetButton" @get-country="getCovidCountryData" @clear-select="clearCountryData" />    
          <StatsContent :data="data" />
          <FooterLinks />
      </div>     
    </div>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import StatsTitle from './components/StatsTitle.vue'
import StatsContent from './components/StatsContent.vue'
import StatsSelect from './components/StatsSelect.vue'
import FooterLinks from './components/FooterLinks.vue'
import './assets/tailwind.css';

export default {
  name: 'App',
  components: {
    Header, 
    StatsTitle, 
    StatsContent, 
    StatsSelect, 
    FooterLinks
  },
  data() {
    return {
      loading: true,
      appName: 'COVID-19 statistics',
      dateTitle: '',
      dataDate: '',
      data: {},
      dataCountries: {},
      resetButton: false
    }
  },
  created() {
    this.getCovidData();
  },
  methods: {
    getCovidData() {
      this.$http.get('https://api.covid19api.com/summary')
      .then(response => {
        this.dateTitle = 'Global';
        this.dataDate = response.data.Global.Date; 
        this.data = response.data.Global;
        this.dataCountries = response.data.Countries;
        this.loading = false;
      })
      .catch(error => {
        console.log(error)
      })
    },
    getCovidCountryData(country){
      this.dateTitle = country.Country;
      this.dataDate = country.Date;
      this.data = country;
      this.resetButton = true;
    },
    clearCountryData() {
      this.loading = true;
      this.getCovidData();
      this.resetButton = false;
    }
  }
}
</script>


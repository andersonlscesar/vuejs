<template>
  <div class="container p-3">

    <h1>Lista de pesquisa</h1>

    <!-- Formulário pesquisa -->

    <form action="">
      <input type="text" class="form-control" placeholder="Pesquisar ..." @input="filter($event)">
    </form>

    <span v-if="inputValue" class="badge bg-primary mt-3 "><strong>{{ inputValue }} - {{ results }}</strong></span>

    <!-- Lista de países -->

    <ol class="list-group list-group-numbered mt-5">
      <li class="list-group-item d-flex justify-content-between align-items-start" v-for="country in countriesSearch" :key="country.id">        
        <div class="ms-2 me-auto">
          <div class="fw-bold">{{ country.name }} </div>
        </div>
        <span class="badge bg-primary rounded-pill">{{ formatPopulationNumber( country.population ) }}</span>
      </li>
    </ol>   


  </div>
</template>

<script>

import  'bootstrap/dist/css/bootstrap.css';

export default {

  name: 'App',

  data() {
    return {

      countries: [
                    { id: 1, name: 'Afeganistão', population: 38928341 },
                    { id: 2, name: 'África do Sul', population: 59308690 },
                    { id: 3, name: 'Albânia', population: 2877797 },
                    { id: 4, name: 'Alemanha', population: 83783942 },
                    { id: 5, name: 'Andorra', population: 77265 },
                    { id: 6, name: 'Angola', population: 32866272 },
                    { id: 7, name: 'Arábia Saudita', population: 34813871 },
                    { id: 8, name: 'Argentina', population: 45195777 },
                    { id: 9, name: 'Armênia', population: 2963234 },
                    { id: 10, name: 'Austrália', population: 25499884 },
                    { id: 11, name: 'Áustria', population: 9006398 },
                    { id: 12, name: 'Azerbaijão', population: 10139177 },
                    { id: 13, name: 'Bahamas', population: 393244 },
                    { id: 14, name: 'Bangladesh', population: 164689383 },
                    { id: 15, name: 'Barbados', population: 287375 },
                    { id: 16, name: 'Bélgica', population: 11589623 },
                    { id: 17, name: 'Belize', population: 397621 },
                    { id: 18, name: 'Benin', population: 12123198 },
                    { id: 19, name: 'Bielorrússia', population: 9449323 },
                    { id: 20, name: 'Bolívia', population: 11673021 },
                    { id: 21, name: 'Bósnia e Herzegovina', population: 3280815 },
                    { id: 22, name: 'Brasil', population: 212559417 },
                    { id: 23, name: 'Brunei', population: 437479 },
                    { id: 24, name: 'Bulgária', population: 6948445 },
                    { id: 25, name: 'Burkina Faso', population: 20903278 },
                    { id: 26, name: 'Burundi', population: 11890784 },
                    { id: 27, name: 'Butão', population: 771612 },
                    { id: 28, name: 'Cabo Verde', population: 555987 },
                    { id: 29, name: 'Camboja', population: 16718965 },
                    { id: 30, name: 'Camarões', population: 26545863 }
                  ],
      countriesSearch: [],  

      inputValue: '',
      results: 0
      
    }
  },

  created() {
    this.countriesSearch = [...this.countries]
  },

  methods: {

    formatPopulationNumber( populationNumber ) {
      return populationNumber.toLocaleString( 'pt-BR' );
    },
     
    filter( $event ) {
      this.inputValue = $event.target.value;
      this.inputValue ?  this.countriesSearch = this.countries.filter((obj) => obj.name.toLocaleLowerCase().includes( this.inputValue.toLocaleLowerCase() ) ) : this.countriesSearch = this.countries;
      this.results = this.countriesSearch.length;
    },
  }
}

</script>



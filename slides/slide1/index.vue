<i18n>
  {
    
  }
</i18n>

<template>
  <wiz-slide>
    <wiz-container class="pa" id="wrapper">
      <wiz-container class="pa" id="container">

    <wiz-list class="pa" id="filtered">
      <wiz-list-item
      v-for="(people, index) in positionFilter"
      :key="index"
      :text="`${people.firstName} ${people.lastName}`"></wiz-list-item>
    </wiz-list>

      <select size="1" v-model="filteredValue">
        <option disabled >Who`s next?</option>
        <option  value="Program Manager">Program Manager</option>
        <option value="Technical Manager">Technical Manager</option>
        <option value="Team Lead">Team Lead</option>
        <option value="QA Engineer">QA Engineer</option>
        <option value="Developer" >Developer</option>
      </select>

      </wiz-container>
    </wiz-container>
  </wiz-slide>
</template>

<script>
export default {
 data() {
   return {
     filteredValue: '',
     peoples: [ 
      { firstName: 'Anna', lastName: 'Tsurukina', position: 'Program Manager' },
      { firstName: 'Anna', lastName: 'Radkevich', position: 'Technical Manager' }, 
      { firstName: 'Ihor', lastName: 'Shevtsov', position: 'Team Lead' }, 
      { firstName: 'Alena', lastName: 'Nesterova', position: 'QA Engineer' }, 
      { firstName: 'Oksana', lastName: 'Ostrovskaya', position: 'QA Engineer' }, 
      { firstName: 'Eugeniy', lastName: 'Garichev', position: 'Developer' }, 
      { firstName: 'Oleg', lastName: 'Merguriev', position: 'Developer' }, 
      { firstName: 'Olga', lastName: 'Pinchuk', position: 'Developer' }, 
      { firstName: 'Roman', lastName: 'Ivanyuk', position: 'Developer' }, 
      { firstName: 'Vitaliy', lastName: 'Bilyavskiy', position: 'Developer' }, 
      { firstName: 'Andrew', lastName: 'Fedotiuk', position: 'Developer' }, 
      { firstName: 'Oleksii', lastName: 'Vityuk', position: 'Developer' } 
    ]
   }
 },
 computed: {
   positionFilter() {
     return this.peoples.filter(people => people.position.includes(this.filteredValue)) 
   }
 }

};
</script>

<style scoped>

  #wrapper{
    width: 320px;
    height: 470px;
    background: #fff;
    top: 140px;
    left: 360px;
  }

  #container {
    background: #fff;
    width: 300px;
    height: 450px;
    align-items: center;
    border-radius: 5px;
    overflow: hidden;
    top: 5px;
    left: 4px;
    border-left: 5px solid #c2c2c2;
    border-bottom: 7px solid #c2c2c2;
    border-right: 7px solid #d2cccc;
  }

  select {
    width: 100%;
    height: 45px;
    padding: 5px 10px;
    -webkit-appearance: none;
    -moz-appearance: none;
    appearance: none;
    border-color: transparent;
    border-bottom: 1px solid #dedddd;
    background: transparent;
  }

  #filtered {
    top: 70px;
  }

  #filtered >>> .wiz-text{
    font-size: 22px;
    /* border-bottom: 1px dotted #dedddd;
    display: inline-block;
    width: 100%; */
  }
  
</style>
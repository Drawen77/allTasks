<i18n>
  {
    "eng": {
      "title": "Second Task"
    }
  }
</i18n>

<template>
  <wiz-slide>
    <wiz-text id="title" :text="$t('title')"></wiz-text>

  <form>
    <input type="text" id="inputType" name="forms" placeholder="Type" v-model="inputType" @keypress="search">
    <input type="text" id="inputId" name="forms" placeholder="Id" v-model="inputId" >
    <input type="number" id="inputCount" name="forms" placeholder="Count" v-model="inputCount" >
  </form>

<div class="wrap">
  <ul>
    <li v-for="(dataItem, index) in ourData" :key="index" >
     <b>id:</b> {{ dataItem.id }} <br/> <b>title:</b> {{ dataItem.title }}<br/> <b>body:</b> {{ dataItem.body }} <br/>{{ dataItem.url }}
    </li>
  </ul></div>
  

  </wiz-slide>
</template>


<script>
export default {
  data() {
    return {
      ourData: [],
      jsonplaceholder: "https://jsonplaceholder.typicode.com",
      inputType: null,
      inputId: null,
      inputCount: 10

    }
  },
  methods: {
    search(e) {
      if (e.key == "Enter") {
        fetch(`${this.jsonplaceholder}${this.inputType}?_limit=${this.inputCount}`)
          .then(res => {
            return res.json();
          }).then(this.setResults)
        // .then(response => this.ourData = response.data)
        .catch(console.error())
      }
    },
    setResults(results) {
      this.ourData = results
    }
  }
};
</script>


<style scoped>

.wrap{
  /* overflow: scroll; */
  padding-bottom: 15px;
  min-height: 50px;
}

  form {
    display: flex;
    flex-direction: column;
    width: 200px;
    margin: 100px auto;
  }

  input {
    margin-bottom: 10px;
  }

  ul {
    display: flex;
    flex-wrap: wrap;
    gap: 15px;
  }

  li {
  border: 1px solid #ccc;
  border-radius: 5px;
  list-style-type: none;
  padding: 5px;
  max-width: 250px;
}

</style>

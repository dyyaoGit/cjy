<template>
  <div class="hello">
    <checkBox v-model="arr" :options="mockData" />
  </div>
</template>

<script>
import checkBox from './demo'

export default {
  name: 'HelloWorld',
  components: {
    checkBox
  },
  data () {
    return {
      mockData: [
        {
          id: '001',
          date: '3',
          price: 998
        },
        {
          id: '002',
          date: '4',
          price: 999
        }
      ],
      arr: []
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

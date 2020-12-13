<template>
  <div class="hello">
    <div v-for="(item, index) in characters.results" :key="index">
      {{item.name}}
    </div>
    <!-- <ApolloQuery :query="require('../graphql/users.gql')">
      <template v-slot="{ result: { loading, error, data } }">
        <div v-if="loading">
          Loading...
        </div>
        <div v-if="error">
          Could not retrieve data, try again later.
        </div>
        <div v-if="data">
          <div v-for="(item, index) in characters.results" :key="index">
            {{item.name}}
          </div>
        </div>
      </template>
    </ApolloQuery> -->
  </div>
</template>

<script>
//
import gql from 'graphql-tag'

export default {
  name: 'HelloWorld',
  //Apollo Client Code
  apollo: {
    characters: gql`
      query{
        characters{
          ...ress
        }
      }


      fragment ress on Characters{
        results{
            id
            name
          }
      }
    `
  },

  data(){
    return{
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
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

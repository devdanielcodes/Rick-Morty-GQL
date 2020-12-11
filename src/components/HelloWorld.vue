<template>
  <div class="hello">
    <!-- <div v-if="$apollo.loading">
      Loading...
    </div>
    <div v-else v-for="book in books" :key="book.id">
      {{book.title}}
    </div> -->
    <ApolloQuery :query="require('../graphql/users.gql')">
      <template v-slot="{result : {loading, error, data}}">
        <div v-if="data">
          <div v-for="book in books" :key="book.id">
            {{book.title}}
          </div>
        </div>
      </template>
    </ApolloQuery>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  name: 'HelloWorld',
  //Apollo Client Code
  apollo: {
    books: gql`
    query{
      books{
        id
        title
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

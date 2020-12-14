<template>
  <div class="hello">
    <nav>
      <img src="../assets/logo.svg" alt="">

      <div class="links">
        <a href="" target="_blank">Github</a>
        <a href="" target="_blank">Dev</a>
      </div>
    </nav>
    <div class="main">
      <div class="heading">
        <h1>RICK AND MORTY CHARACTERS</h1>
        <img src="../assets/h-line.svg" alt="">
      </div>
      <p>Created with Vue and GraphQL API</p>
      <img class="hero" src="../assets/hero.svg" alt="">
    </div>
    <div class="characters">
      <div class="heading">
        <h2>CHARACTERS</h2>
        <img src="../assets/h-line.svg" alt="">
      </div>
      <div class="aside">
        <h2>Main</h2>
        <div class="casts">
          <div class="cast" v-for="(item, index) in characters.results" :key="index">
            <img class="cast_img" :src="item.image" alt="">
            <span class="cast_top"><h4>{{item.name}}</h4> <p>{{item.species}}</p></span>
            <p>{{item.origin.name}}</p>
            <h3 class="cast_gen"><span>Gender</span><span>{{item.gender}}</span></h3>
          </div>
        </div>
      </div>
    </div>
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
            image
            gender
            species
            origin{
              name
            }
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
nav{
  display: flex;
  justify-content: space-around;
  align-items: center;
  height: 10vh
}
nav .links a{
  display: inline-block;
  margin-right: 20px;
  color: black;
  text-decoration: none;
}
.main{
  text-align: center
}

.heading{
  position: relative;
  font-size: 25px;
  text-align: center;
  margin-top: 50px;
}
.heading h1{
  font-weight: 400
}
.heading img{
  position: absolute;
  bottom: -70%;
  left: 50%;
  width: 600px;
  transform: translateX(-50%)
}
.hero{
  width: 600px
}
.characters .heading img{
  bottom: -40%;
  width: 300px
}

.aside{
  width: 90%;
  min-height: 100vh;
  margin: 40px auto;
  background: #046064;
  border: 20px solid #23BCC2;
  border-radius: 60px;
  color: white;
}
.aside h2{
  margin: 40px
}
/* -- */


.casts{
  display: flex;
  justify-content: space-around;
  flex-wrap: wrap
}
.cast{
  padding: 25px;
  background: #2C797C;
  width: 200px;
  border-radius: 40px;
  margin: 20px 10px;
}
.cast_img{
  border-radius: 20px;
  width: 100%;
}
.cast_top{
  display: flex;
  justify-content: space-between;
  align-items: center;
}
.cast_top h4{
  font-weight: 500;
  font-size: 16px
}
.cast_top p{
  font-size: 12px;
  border-radius: 200px;
  background: #046064;
  padding: 5px 10px;
}
.cast_gen{
  display: flex;
  justify-content: space-between;
  align-items: center;
  font-weight: 200
}

@media(max-width: 781px){
  .heading{
    position: relative;
    font-size: 18px;
    text-align: center;
    margin-top: 50px;
  }
  .heading h1{
    font-weight: 400
  }
  .heading img{
    position: absolute;
    bottom: -50%;
    left: 50%;
    width: 350px;
    transform: translateX(-50%);
    z-index: -1;
  }
  .hero{
    width: 330px
  }
  .characters .heading img{
    bottom: -40%;
    width: 300px
  }
}
@media(max-width: 571px){
  .heading{
    position: relative;
    font-size: 15px;
    text-align: center;
    margin-top: 50px;
  }
}
@media(max-width: 480px){
  .heading img{
    bottom: -20%;
    width: 280px;
  }
  .hero{
    width: 300px
  }
}
</style>

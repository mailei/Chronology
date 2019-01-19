<template>
  <!-- <div class="movies">
    <h1>年表</h1>
    <div v-for="movie in movies" v-bind:key="movie.id" class="movie">
      <img v-bind:src="movie.poster" class="poster">
      <div>
        <strong>{{movie.name}}</strong>, <i>{{movie.director}}</i> [{{movie.year}}]
        <router-link :to="{ name: 'show', params: { id: movie.id }}">더보기</router-link>
      </div>
  </div>-->
  <div id="timeline">
    <ul id="datas">
      <li v-for="(value, key, index) in dates" :key="index">
        <a :href="'#'+chrono.year">{{chrono.year}}</a>
      </li>
    </ul>
    <ul id="datas">>
      <li v-for="(chrono, key, index) in dates" :key="index" v-bind:id="chrono.year">
        <img :src="'images/'+chrono.images+'.png'" width="256" height="256">
        <h1>{{chrono.year}}</h1>
        <h2>{{chrono.title}}</h2>
        <p>{{chrono.text}}</p>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  created () {
    this.$http.get('/chrono').then(response => {
      this.datas = response.data
    })
  },
  name: 'chronology',
  data () {
    return {
      dates: []
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.poster {
  width: 185px;
  vertical-align: middle;
}

.movie {
  display: inline-block;
  padding: 10px;
  text-align: center;
}
</style>

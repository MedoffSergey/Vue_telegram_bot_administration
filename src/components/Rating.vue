<template lang='pug'>
.container
	table.table.mt-3
		thead.thead-light
			tr
				th(scope='col') №
				th(scope='col') Id
				th(scope='col') First Name
				th(scope='col') Emotions


		tr(scope='row' v-for='(user, index) in ratingList.sortRating' :key='index')
			td {{ index+1 }}
			td {{ user.id }}
			td {{ user.name }}
			td {{ user.sum }}
</template>


<script>
import axios from 'axios';

export default {

  data() {
    return {
      ratingList: []
    }
  },
  mounted() {
    this.refreshRatingList() // Вызываем methods refreshRatingList для обновления списка пользователей
  },

  methods: {
    refreshRatingList() { //получаем таблицу с пользователями
      axios.get('http://localhost:3000/rating')
        .then(response => (this.ratingList = response.data))
    }
  }
}
</script>

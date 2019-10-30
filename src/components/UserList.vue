<template lang='pug'>
.container
	table.table.mt-3
		thead.thead-light
			tr
				th(scope='col') №
				th(scope='col') Id
				th(scope='col') First Name
				th(scope='col') Username

			tr(scope='row' v-for='(user, index) in userList' :key='index')
				td {{ index+1 }}
				td {{ user.id }}
				td {{ user.name }}
				td {{ user.username }}
</template>


<script>
import axios from 'axios';

export default {
	props: ['page'],
  data() {
    return {
      userList: []
    }
  },
		mounted() { // Функция загрузки данных
			this.refreshUserList() // Вызываем methods refreshRatingList для обновления списка пользователей
			localStorage.setItem('localStoragePage',this.page)
			this.page = localStorage.getItem(this.localStoragePage)
	},


  methods: {
    refreshUserList() { //получаем таблицу с пользователями
      axios.get('http://localhost:3000/userList')
        .then(response => (this.userList = response.data))
    }
  }
}
</script>

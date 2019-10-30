<template lang='pug'>
.container-fluid
	table.table.mt-3
		thead.thead-light
			tr
				th(scope='col') First Name
				th(scope='col') Last Name
				th(scope='col') Text
				th(scope='col') Date
				th(scope='col') Reply First Name
				th(scope='col') Reply Last Name
				th(scope='col') Reply Message
				th(scope='col') Emotions

		tr(scope='row' v-for='(user, index) in historyList' :key='index')
			td {{ user.first_name }}
			td {{ user.last_name }}
			td {{ user.msg_text }}
			td {{ newDate(user.date) }}
			td {{ user.reply_first_name }}
			td {{ user.reply_last_name }}
			td {{ user.reply_message }}
			td {{ user.emotions }}
</template>


<script>
import axios from 'axios';

export default {
	props: ['page'],
  data() {
    return {
      historyList: []
    }
  },
  mounted() { // Функция загрузки данных
    this.refreshHistoryOptionList() // Вызываем methods refreshRatingList для обновления списка пользователей
		localStorage.setItem('localStoragePage',this.page)
		this.page = localStorage.getItem(this.localStoragePage)
  },
  methods: {
    newDate(date) {
      let time = new Date(date * 1000).getHours() + " часов " + new Date(date * 1000).getMinutes() + " минут"
      return time
    },
    refreshHistoryOptionList() { //получаем таблицу с пользователями
      axios.get('http://localhost:3000/history')
        .then(response => (this.historyList = response.data))
    }
  }
}
</script>

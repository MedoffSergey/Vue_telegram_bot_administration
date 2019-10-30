<template lang='pug'>
div <!--Должен быть обернут в один div / рендерим компоненты -->
	navbar(@showHistory = 'showHistory'  @showRating = 'showRating'  @showUsers = 'showUsers')
	div(v-if="page=='Rating'")
		rating(:page = 'page')
	div(v-if="page=='History'")
		historyOption(:page = 'page')
	div(v-if="page=='Users'")
		userlist(:page = 'page')
</template>


<script>

import navbar from './components/Navbar.vue';
import rating from './components/Rating.vue';
import historyOption from './components/HistoryOption.vue';
import userlist from './components/UserList.vue';

export default {
  name: 'app',

  components: { // Добавим локальные компоненты
    navbar,
    rating,
    historyOption,
		userlist
  },

  data() { // Переменные которые можно использовать в шаблоне
    return {
      page: "",
			localStoragePage : ''
    }
  },

		mounted() { // Функция загрузки данных
			this.page = localStorage.getItem('localStoragePage')
	},
  methods: {
		showHistory() {
			this.page = 'History'
		},
		showRating() {
			this.page = 'Rating'
		},
		showUsers() {
			this.page = 'Users'
		}
  }
}
</script>

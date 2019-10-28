<template lang='pug'>
	div <!--Должен быть обернут в один div / рендерим компоненты -->
		rating( :ratingList = 'ratingList' )
		historyOption(:historyList = 'historyList')
</template>


<script>
import axios from 'axios'; //Импортируем компоненты

import rating from './components/Rating.vue';
import historyOption from './components/HistoryOption.vue';

export default {
  name: 'app',

  components: { // Добавим локальные компоненты
    rating,
		historyOption
  },

  data() { // Переменные которые можно использовать в шаблоне
    return {
      ratingList: [],
			historyList: []
    }
  },



  mounted() { // Функция загрузки данных
    this.refreshRatingList() // Вызываем methods refreshRatingList для обновления списка пользователей
    this.refreshHistoryOptionList() // Вызываем methods refreshHistoryOptionList для обновления списка истории мнений
  },
  methods: {
    refreshRatingList() { //получаем таблицу с пользователями
      axios.get('http://localhost:3000/rating')
        .then(response => (this.ratingList = response.data))
    },
		refreshHistoryOptionList() { //получаем таблицу с пользователями
      axios.get('http://localhost:3000/history')
        .then(response => (this.historyList = response.data))
    },
  }
}

</script>

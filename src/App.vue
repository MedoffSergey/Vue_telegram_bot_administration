<template lang='pug'>
div <!--Должен быть обернут в один div / рендерим компоненты -->
	navbar(@showHistory = 'showHistory'  @showRating = 'showRating')
	div(v-if="page=='Rating'")
		rating()
	div(v-if="page=='History'")
		historyOption()
</template>


<script>

import navbar from './components/Navbar.vue';
import rating from './components/Rating.vue';
import historyOption from './components/HistoryOption.vue';

export default {
  name: 'app',

  components: { // Добавим локальные компоненты
    navbar,
    rating,
    historyOption
  },

  data() { // Переменные которые можно использовать в шаблоне
    return {
      page: "home"
    }
  },

  methods: {
		showHistory() {
			this.page = 'History'
		},
		showRating() {
			this.page = 'Rating'
		}
  }
}
</script>

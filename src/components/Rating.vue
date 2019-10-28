<template lang='pug'>
.container

  table.table.mt-3
    thead.thead-light
      tr
        th(scope='col') Id
        th(scope='col') First Name
        th(scope='col') Last Name


    tr(scope='row' v-for='(user, index) in ratingList' :key='index')
      td {{ user }}
</template>


<script>
  export default {
    props: ['ratingList' ],  // массив с App.vue
    data(){
      return {
      }
    }
}
</script>

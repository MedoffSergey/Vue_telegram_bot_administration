<template lang='pug'>
div
	b-navbar.navbar.navbar-expand-lg.navbar-dark.bg-primary.sticky-top(toggleable="lg"  variant="primary")
		b-navbar-brand(href="/")
			a.font-italic.font-wid BOTIK
		b-navbar-toggle(target="nav-collapse")
		b-collapse#nav-collapse(is-nav="")
			b-navbar-nav.h5
				b-nav-item(href="#" @click='showHistoryTable') History
				b-nav-item(href="#" @click='showRatingTable') Rating
				b-nav-item(href="#" @click='showUsersTable') Users
</template>


<script>
export default {
  methods: {
    showHistoryTable() {
      this.$emit("showHistory")
    },
    showRatingTable() {
      this.$emit("showRating")
    },
		showUsersTable() {
			this.$emit("showUsers")
		}
  }
}
</script>

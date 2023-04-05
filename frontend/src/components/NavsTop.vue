<template lang="pug">
header.py-3.mb-4.border-bottom
  .container.head-container
    .row.col-12.justify-content-end
      .d-flex.col-xl-8.col-lg-12.col-md-12.col-sm-12.col-12
        ul.nav.col-12.justify-content-center.mt-auto.mb-auto
          li.nav-li
            a.nav-link.link-secondary(href='#') Каталог
          li.nav-li
            a.nav-link.link-dark(href='#') Доставка
          li.nav-li
            a.nav-link.link-dark(href='#') Оплата
          li.nav-li
            a.nav-link.link-dark(href='#') Контакты
          li.nav-li
            a.nav-link.link-dark(href='#') О компании
      .col-xl-4.col-lg-12.col-md-12.col-sm-12.col-12.mt-xl-0.mt-lg-3.mt-md-3.mt-sm-3.test
        .form-inline.d-flex.justify-content-center.mt-auto.mb-auto
          input.dropdown-toggle.search-input.form-control(data-bs-toggle='dropdown' aria-expanded='false' id="dropdownMenuButton1" v-model="searchInput" placeholder='Поиск по названию картины' aria-label='Search')
          .dropdown
            ul.dropdown-menu.custom-dropdown(aria-labelledby='dropdownMenuButton1')
              li(v-for="i in searchResult")
                span.dropdown-item.custom-item(data-bs-toggle='modal' :data-bs-target='`#exampleModal${i.id}`') {{i.name}}
              li(v-if="!searchResult[0]")
                span.ps-3.pe-3 Ничего не найдено
          button.btn() Найти
</template>

<script>
export default {
  props: {
    searchContent: Array
  },
  data() {
    return {
      searchInput: '',
      searchResult: [],
      cardIdArr: this.$_getAllId()
    }
  },
  methods: {
    $_getAllId() {
      let cardIdArr = []
      for (let i in this.searchContent) {
        cardIdArr.push(`card-content${this.searchContent[i].id}`)
      }
      return cardIdArr
    }
  },
  watch: {
    searchInput: function (val) {
      val = val.toLowerCase()
      this.searchResult = this.searchContent.filter((item) => {
        let element = document.getElementById(`card-content${item.id}`)
        if (item.name.toLowerCase().indexOf(val) > -1) {
          element.classList.remove('hide')
          return true
        } else {
          element.classList.add('hide')
        }
      })
      if (!val) {
        this.searchResult = []
        for (let i in this.cardIdArr) {
          let element = document.getElementById(`${this.cardIdArr[i]}`)
          element.classList.remove('hide')
        }
      }
    }
  }
}
</script>

<style scoped>
.head-container {
  padding-left: 5px;
  padding-right: 5px;
}
.nav-li a {
  padding-right: 28px;
  padding-left: 28px;
}

ul.custom-dropdown {
  width: 299px;
  border-radius: 0;
}

.custom-item:active {
  background: #9F9F9F;
}
</style>

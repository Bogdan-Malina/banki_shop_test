<template lang="pug">
footer.py-3
  .container.footer-container
    .row.col-12
      .d-flex.col-xl-8.col-lg-12.col-md-12.col-sm-12.col-12
        ul.nav.col-12.justify-content-center
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
      .d-flex.col-xl-4.col-lg-12.col-md-12.col-sm-12.col-12.mt-xl-0.mt-lg-3.mt-md-3.mt-sm-3.test.justify-content-center
        span.footer-data.phone
          img.logo(src="../img/phone.png")
          span.logo +7 (812) 555-55-55
        span.footer-data.map
          img.logo(src="../img/map.png")
          span г. Санкт-Петербург, ул. Ефимова, 3
</template>

<script>
export default {
  props: {
    msg: String
  },
}
</script>

<style scoped>
.footer-container {
  padding-left: 4px;
  padding-right: 5px;
}
.nav-li a {
  padding-right: 28px;
  padding-left: 28px;
}
.footer-data {
  margin-top: auto;
  margin-bottom: auto;
  font-style: normal;
  font-weight: 400;
  font-size: 14px;
  line-height: 150%;
  color: #555555;
}

.phone {
  min-width: 155px;
}
.map {
  margin-right: -50px;
  min-width: 275px;
}
</style>

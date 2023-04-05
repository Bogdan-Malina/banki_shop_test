<template lang="pug">
.card.custom-card.position-relative.col-12
  .sales(v-if="!content.in_stock" data-bs-toggle='modal' :data-bs-target='`#exampleModal${content.id}`')
  img.card-img-top.custom-card-img(:src='content.img' alt='Card image cap' data-bs-toggle='modal' :data-bs-target='`#exampleModal${content.id}`')
  .card-body.custom-card-body
    .name-div(data-bs-toggle='modal' :data-bs-target='`#exampleModal${content.id}`')
      h1.name-author.mb-0.text-start «{{ content.name }}»
      h1.name-author.mb-4.text-start {{ content.author }}
    .price-and-order.d-flex(v-if="content.in_stock")
      .price-div.mb-auto.mt-auto
        p.old_price.mb-0(v-if="content.old_price")  {{ content.old_price }} $
        p.price.mb-0 {{ content.price }} $
      .btn-div.ms-auto.position-relative
        .sales(v-if="spinner" )
          .spinner-border.custom-spinner(role='status')
        button.btn(@click="$_addToBasket" v-if="!in_basket") Купить
        button.btn.inBasket(@click="$_addToBasket" v-else)
          img.logo(src="../img/inBasket.png")
          span.mt-auto.mb-auto В корзине
    .mt-auto.mb-auto(v-else)
      h1.sell.mb-0 Продана на аукционе

  .modal.fade(:id="`exampleModal${content.id}`" tabindex='-1' aria-labelledby='exampleModalLabel' aria-hidden='true')
    .modal-dialog
      .modal-content
        .modal-header
          h3#exampleModalLabel.modal-title «{{ content.name }}»
          button.btn-close(type='button' data-bs-dismiss='modal' aria-label='Закрыть')
        .modal-body
          .carousel-modal
            .carousel.slide(:id="`carouselExampleControls${ content.id }`" data-bs-ride='carousel')
              .carousel-inner
                .carousel-item.active
                  img.d-block.w-100(:src='content.img' alt='...')
                .carousel-item
                  img.d-block.w-100(:src='content.img' alt='...')
                .carousel-item
                  img.d-block.w-100(:src='content.img' alt='...')
              button.carousel-control-prev(type='button' :data-bs-target="`#carouselExampleControls${ content.id }`" data-bs-slide='prev')
                span.carousel-control-prev-icon(aria-hidden='true')
                span.visually-hidden Previous
              button.carousel-control-next(type='button' :data-bs-target="`#carouselExampleControls${ content.id }`" data-bs-slide='next')
                span.carousel-control-next-icon(aria-hidden='true')
                span.visually-hidden Next

            .modal-text.mt-4.ps-3.pe-3.text-start
              p.border-bottom.pb-3 {{ content.desc }}
            .d-flex.pb-3.pt-2.ps-3.pe-3
              .text-start.mt-auto.mb-auto
                h3.mt-2 Автор: {{content.author}}
                h3(v-if="content.in_stock") Цена: {{content.price}}$
              .btn-div.mt-auto.mb-auto.ms-auto.position-relative(v-if="content.in_stock")
                .sales(v-if="spinner" )
                  .spinner-border.custom-spinner(role='status')
                button.btn(@click="$_addToBasket" v-if="!in_basket") Купить
                button.btn.inBasket(@click="$_addToBasket" v-else)
                  img.logo(src="../img/inBasket.png")
                  span.mt-auto.mb-auto В корзине
</template>

<script>
export default {
  props: {
    painting: Object
  },

  data() {
    return {
      content: this.painting,
      in_basket: 0,
      spinner: 0
    }
  },

  methods: {
    $_getPrice: function() {
      if (this.content.price) {
        this.content.price = this.content.price.toLocaleString('ru-RU')
      }
      if (this.content.old_price ) {
        this.content.old_price = this.content.old_price.toLocaleString('ru-RU')
      }
    },

    async $_addToBasket() {
      let promise = new Promise((resolve) => {
        this.spinner = 1
        setTimeout(() => {
          this.spinner = 0
          resolve("result");
        }, 2000);
      });
      promise.then(() => {
          if (localStorage.basket) {
            let basket = localStorage.getItem('basket').split(',')
            if (this.in_basket) {
              let value = this.content.id+''
              basket = basket.filter(function(item) {
                return item !== value
              })
              localStorage.setItem('basket', basket);
              this.in_basket = 0
            } else {
              basket.push(this.content.id)
              localStorage.setItem('basket', basket);
              this.in_basket = 1
            }
          } else {
            localStorage.setItem('basket', this.content.id);
            this.in_basket = 1
          }
        }
      )
    },

    $_checkLocalStorage() {
      if (localStorage.basket) {
        let basket = localStorage.getItem('basket').split(',')
        if (basket.includes(this.content.id+'')) {
          this.in_basket = 1
        }
      } else {
        console.log('НЕТ ХРАНИЛИЩА')
      }
    }
  },
  created: function(){
    this.$_getPrice()
    this.$_checkLocalStorage()
  }
}
</script>

<style scoped>
.custom-card {
  border-radius: 0;
  min-width: 280px;
}

img.custom-card-img {
  object-fit: cover;
  height: 160px;
  border-radius: 0;
  cursor: pointer;
}

.custom-card-body {
  max-height: 168px;
  min-height: 168px;
}

.name-author {
  font-style: normal;
  font-weight: 400;
  font-size: 18px;
  line-height: 150%;
}
.old_price {
  font-style: normal;
  font-weight: 300;
  font-size: 14px;
  line-height: 150%;
  text-decoration-line: line-through;

  display: flex;
  color: #A0A0A0;
}

.price {
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;
}

.sell {
  font-style: normal;
  font-weight: 700;
  font-size: 16px;
  line-height: 150%;

  display: flex;
  align-items: center;

  color: #343030;
}

.sales {
  cursor: pointer;
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  background-color: white;
  opacity: .4;
}

.inBasket {
  background: #5B3A32;
  padding-left: 8px;
  padding-right: 7px;
}

.inBasket img {
  width: 16px;
  height: 15px;
  margin-right: 4px;
  margin-bottom: 2px;
}

.name-div {
  cursor: pointer;
}

.custom-spinner {
  width: 30px;
  height: 30px;
  margin-top: 10px;
}
</style>

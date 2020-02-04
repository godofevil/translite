<template>
  <div id="app">
      <div class="wrap">
          <input type="search" class="text__en" v-model="textEn">
          <input v-model="translit" class="text__ru" readonly>
          <button v-on:click="copyText" class="copy">Copy</button>
      </div>
  </div>
</template>

<script>
export default {
    name: 'app',
    data() {
        return {
            textEn: '',
            textRu: []
        }
    },
    methods: {
        copyText(){
            document.querySelector('.text__ru').select();
            document.execCommand('copy');
        }
    },
    computed: {
        translit: function() {
            return this.textRu = this.textEn.split('').map(item => {
                (item == 'ё') && (item = '`'); (item == 'Ё') && (item = '~');
                (item == 'й') && (item = 'q'); (item == 'Й') && (item = 'Q');
                (item == 'ц') && (item = 'w'); (item == 'Ц') && (item = 'W');
                (item == 'у') && (item = 'e'); (item == 'У') && (item = 'E');
                (item == 'к') && (item = 'r'); (item == 'К') && (item = 'R');
                (item == 'е') && (item = 't'); (item == 'Е') && (item = 'T');
                (item == 'н') && (item = 'y'); (item == 'Н') && (item = 'Y');
                (item == 'г') && (item = 'u'); (item == 'Г') && (item = 'U');
                (item == 'ш') && (item = 'i'); (item == 'Ш') && (item = 'I');
                (item == 'щ') && (item = 'o'); (item == 'Щ') && (item = 'O');
                (item == 'з') && (item = 'p'); (item == 'З') && (item = 'P');
                (item == 'х') && (item = '['); (item == 'Х') && (item = '{');
                (item == 'ъ') && (item = ']'); (item == 'Ъ') && (item = '}');

                (item == 'ф') && (item = 'a'); (item == 'Ф') && (item = 'A');
                (item == 'ы') && (item = 's'); (item == 'Ы') && (item = 'S');
                (item == 'в') && (item = 'd'); (item == 'В') && (item = 'D');
                (item == 'а') && (item = 'f'); (item == 'А') && (item = 'F');
                (item == 'п') && (item = 'g'); (item == 'П') && (item = 'G');
                (item == 'р') && (item = 'h'); (item == 'Р') && (item = 'H');
                (item == 'о') && (item = 'j'); (item == 'О') && (item = 'J');
                (item == 'л') && (item = 'k'); (item == 'Л') && (item = 'K');
                (item == 'д') && (item = 'l'); (item == 'Д') && (item = 'L');
                (item == 'ж') && (item = ';'); (item == 'Ж') && (item = ':');
                (item == 'э') && (item = "'"); (item == 'Э') && (item = '"');

                (item == 'я') && (item = 'z'); (item == 'Я') && (item = 'Z');
                (item == 'ч') && (item = 'x'); (item == 'Ч') && (item = 'X');
                (item == 'с') && (item = 'c'); (item == 'С') && (item = 'C');
                (item == 'м') && (item = 'v'); (item == 'М') && (item = 'V');
                (item == 'и') && (item = 'b'); (item == 'И') && (item = 'B');
                (item == 'т') && (item = 'n'); (item == 'Т') && (item = 'N');
                (item == 'ь') && (item = 'm'); (item == 'Ь') && (item = 'M');
                (item == 'б') && (item = ','); (item == 'Б') && (item = '<');
                (item == 'ю') && (item = '.'); (item == 'Ю') && (item = '>');
                return item;
            }).join('');
        }
    }
}
</script>

<style lang="sass">
    $primary-blue: #0d9ee3
    .wrap
        padding: 50px 15px 15px 15px
        display: grid
        grid-template-columns: 100%
        grid-gap: 30px
        justify-items: center
        align-items: center
        font-size: 2rem
    .text__en, .text__ru
        width: 90%
        font-size: 2rem
        outline: 0
        color: $primary-blue
    .text
        &__en
            padding: 20px
            border-radius: 20px
            border: 1px solid $primary-blue
        &__ru
            border: 0
            text-align: center
    .copy
        border: 0
        background: $primary-blue
        font-size: 2rem
        padding: 10px 20px
        color: #fff
        border-radius: 20px
        cursor: pointer
        transition: background .3s
        outline: 0
        &:hover
            background: darken($primary-blue, 10%)
</style>

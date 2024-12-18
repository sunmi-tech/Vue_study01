<script>
import data from './assets/oneroom';
import Card from './components/Card.vue';
import Modal from './components/Modal.vue';
import Banner from './components/Banner.vue';
export default {
  name: 'App',
  data() {
    return {
      menu: ['Home', 'Shop', 'About'],
      oneroom: data,
      oneroomOrigin: [...data],
      modal: false,
      modalIndex: 0,
      showBanner: true,
    }
  },
  components: {
    Card,
    Modal,
    Banner,
  },
  methods: {
    priceSort() {
      this.oneroom.sort(function (a, b) {
        return a.price - b.price
      })
    },
    sortBack() {
      this.oneroom = [...this.oneroomOrigin];
    },
  },
  mounted() {
    setTimeout(() => {
      this.showBanner = false;
    }, 2000);
  },
}
</script>

<template>
  <transition name="fade">
    <Modal @closeModal="modal = false" :oneroom="oneroom" :modal="modal" :modalIndex="modalIndex" />
  </transition>
  <div class="menu">
    <a v-for="(a, i) in menu" :key="i">{{ a }}</a>
  </div>
  <Banner v-if="showBanner == true"></Banner>
  <button @click="priceSort">가격순 정렬</button>
  <button @click="sortBack">되돌리기</button>
  <Card @openModal="modal = true; modalIndex = $event" :oneroom="oneroom[i]" v-for="(a, i) in oneroom" :key="i" />
</template>

<style scoped>
body {
  margin: 0;
}

div {
  box-sizing: border-box;
}

.menu {
  background-color: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.fade-enter-from {
  opacity: 0;
}

.fade-enter-active {
  transition: all 1s;
}

.fade-enter-to {
  opacity: 1;
}

.fade-leave-from {
  opacity: 1;
}

.fade-leave-active {
  transition: all 1s;
}

.fade-leave-to {
  opacity: 0;
}
</style>

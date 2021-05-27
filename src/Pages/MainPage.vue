<template>
  <no-internet-page v-if="showNoInternetPage"></no-internet-page>
  <div v-else>
    <top-button @show-cards="showSelectedCards"></top-button>
    <div  style="display:flex; margin-top: 40px;">
      <div
        v-for="(data, index) in showData" :key="index"
        :style="['width: 25%;', index !==0 ? 'margin-left: 14px' : '', !data.popular ? 'margin-top: 40px' : '']"
      >
        <price-card
          :cardData="data"
        >
        </price-card>
        <bottom-button @click="bottomButtonClicked(data)" :id="`bottom-button-${index}`" :selected="data.popular" :style="[data.popular ? 'margin-top: 40px' : '']">Start Your Trial</bottom-button>
      </div>
    </div>
    <form-model v-if="showModal" :modal-data="modalData" @closeModal="closeModal"></form-model>
  </div>
</template>

<script>
import { ref, onMounted, computed } from 'vue'
import { planData } from '../data/data.js'

import NoInternetPage from '../components/NoInternetPage.vue'
import PriceCard from '../components/PriceCard.vue'
import TopButton from '../components/TopButton.vue'
import BottomButton from '../components/BottomButton.vue'
import FormModel from '../components/FormModel.vue'

export default {
  components: {
    NoInternetPage,
    PriceCard,
    TopButton,
    BottomButton,
    FormModel
  },
  setup () {
    const showNoInternetPage = ref(false)
    const showModal = ref(false)
    const selectData = ref('$300-$400')
    const modalData = ref({})
    const hasNetwork = (onLine) => {
      showNoInternetPage.value = !onLine
    }
    onMounted(() => {
      window.addEventListener("load", () => {
      hasNetwork(navigator.onLine);
    })
    window.addEventListener("online", () => {
        hasNetwork(true);
      })
      window.addEventListener("offline", () => {
        hasNetwork(false);
      })
    })

    const showData = computed(() => {
      return planData[selectData.value]
    })

    const showSelectedCards = (selectedData) => {
      selectData.value = selectedData.value
    }
    const bottomButtonClicked = (data) => {
      console.log('data', data)
      modalData.value = data
      showModal.value = true
    }
    const closeModal = () => {
      showModal.value = false
      modalData.value = {}
    }
    return {
      showNoInternetPage,
      showSelectedCards,
      planData,
      showData,
      BottomButton,
      bottomButtonClicked,
      showModal,
      closeModal,
      modalData
    }
  }
}
</script>

<style lang="scss" scoped>

</style>
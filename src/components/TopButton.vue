<template>
  <div class="top-buttons">
    <div v-for="(button, index) in buttonsList" :key="index" @click="buttonClicked(button)" class="button-wrapper">
      <div :class="['button', button.selected ? 'button-selected' : 'button-not-selected']">
        <div>{{button.text}}</div>
      </div>
    </div> 
  </div>
</template>

<script>
import { ref } from 'vue'
export default {
  emits: ['show-cards'],
  setup (props, {emit}) {
    const buttonsList = ref([
      {
        id: 1, 
        selected: false,
        text: '$100-$200',
        value: '$100-$200'
      },
      {
        id: 2,
        selected: false,
        text: '$200-$300',
        value: '$200-$300'
      },
      {
        id: 3,
        selected: true,
        text: '$300-$400',
        value: '$300-$400'
      },
      {
        id: 4,
        selected: false,
        text: '$400-$500',
        value: '$400-$500'
      },
      {
        id: 5,
        selected: false,
        text: '$500+',
        value: '$500+'
      }
    ])
    const buttonClicked = (data) => {
      buttonsList.value.forEach((button) => {
        button.selected = false
        if (button.id === data.id) {
          button.selected = true
        }
      })
      emit('show-cards', data)
    }
    return {
      buttonsList,
      buttonClicked
    }
  }
}
</script>

<style lang="scss" scoped>
.top-buttons {
  width: 100%;
  height: 55px;
  display: flex;
}
.button {
  height: 55px;
  border-right: 1px solid #bfbdbd;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
}
.button-selected {
  background: #49668c;
  color: white;
}
.button-not-selected {
  background: #e4e8ed;
}
.button-wrapper {
  width: 20%;
  &:first-of-type > div{
    border-top-left-radius: 8px;
    border-bottom-left-radius: 8px;
  }
  &:last-of-type > div {
    border-right: none;
    border-top-right-radius: 8px;
    border-bottom-right-radius: 8px;
  }
}
</style>
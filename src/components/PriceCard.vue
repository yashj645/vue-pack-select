<template>
  <div class="price-card-wrapper">
    <div v-if="cardData.popular" class="price-card-wrapper-popular-tag">
      Most Popular!
    </div>
    <div class="price-card-wrapper-box">
      <div class="price-card-wrapper-box-top">
        Qualified {{cardData.noOfLeads}}
      </div>
      <div :class="['price-card-wrapper-box-body', cardData.popular ? 'is-selected' : '']">
        <div style="font-size:29px">
          {{cardData.pricePerLead}}
        </div>
        <div style="margin-top: 4px;font-size: 12px;">
        Per Qualified lead
        </div>
        <div class="hr-style-card"></div>
        <div style="margin-top: 14px; font-size: 12px;">Qualified Leads Per Month
        </div>
        <div style="margin-top: 4px;">
          {{cardData.noOfLeads}}
        </div>
        <div class="hr-style-card"></div>
        <div style="margin-top: 14px;">
        Platform Fee Per Month
        </div>
        <div style="margin-top: 4px">
          {{cardData.platformFee}}
        </div>
      </div>
      <div v-if="cardData.totalFee" class="price-card-wrapper-box-bottom">
        {{cardData.totalFee}}/mo
      </div>
    </div>
  </div>
</template>

<script>
export default {
  props: {
    cardData: {
      type: Object,
      default: () => {
        return {
          noOfLeads: '40',
          pricePerLead: '$67',
          platformFee: '$599',
          totalFee: '$3279',
          popular: true
        }
      }
    }
  },
  setup () {
    

    return {}
  }
}
</script>

<style lang="scss" scoped>
.price-card-wrapper {
  width: 100%;
  height: 332px;
  box-sizing: border-box;
  &-popular-tag {
    width: 100%;
    height: 40px;
    background: #d95a00;
    color: white;
    display: flex;
    align-items: center;
    justify-content: center;
  }
  &-box {
    width: 100%;
    height: 294px;
    box-sizing: border-box;
    &-top {
      height: 40px;
      width: 100%;
      background: #49668c;
      color: white;
      display: flex;
      align-items: center;
      justify-content: center;
    }
    &-body {
      width: 100%;
      height: 214px;
      background: white;
      text-align: center;
      padding: 18px 0px 0px 0px;
    }
    &-bottom {
      height: 40px;
      width: 100%;
      background: #49668c;
      color: white;
      display: flex;
      font-weight: 500;
      font-size: 18px;
      align-items: center;
      justify-content: center;
    }
  }
}
.is-selected {
  background: #e4e8ed !important; 
}
.hr-style-card {
  margin-left: 32px;
  width: calc(100% - 64px);
  border: 1px dashed #bdbdbd;
  margin-top: 14px;
}
</style>
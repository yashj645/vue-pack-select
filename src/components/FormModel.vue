<template>
  <transition name="modal">
    <div class="modal-mask">
      <div
        class="modal-wrapper"
        ref="modal"
        @keydown.esc="callCloseModal"
        tabindex="0"
      >
        <div class="modal-container">
          <div style="width:100%; display: flex; justify-content: space-between;" class="modal-header">
            <div></div>
            <div style="font-size: 18px; font-weight: 600;">Get Started with SquadVoice</div>
            <div>
              <img
            v-if="showCloseIcon"
              @click="callCloseModal" height="14" width="14" style="cursor: pointer;"
              src="https://www.brandrep.com/assets/public/sections/plans/none.svg" alt=""/>
            </div>
          </div>
          <div style="border-bottom: 1px solid #202124; margin-top: 10px;margin-top: 5px; width: calc(100% - 20px);"></div>
          <div class="modal-body">
            <div>
             <span style="font-weight: 600;">Plan Selected:</span> Qualified {{modalData.noOfLeads}}
            </div>
            <div style="margin-top: 12px;">
              <div style="font-size:12px; margin-bottom:4px;">Name</div>
              <div>
              <input v-model="formData.name" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="input"     autocomplete="off">
              </div>
            </div>
            <div style="display: flex; margin-top: 12px;">
              <div style="width: 49%;">
                <div style="font-size:12px; margin-bottom:4px;">E-mail Address</div>
                <div>
                <input v-model="formData.emailId" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="input" autocomplete="off">
                </div>
              </div>
              <div style="width: 49%; margin-left: 16px;">
                <div style="font-size:12px; margin-bottom:4px;">Phone no.</div>
                <div>
                <input v-model="formData.phoneNumber" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="input" autocomplete="off">
                </div>
              </div>
            </div>
            <div style="display: flex; margin-top: 12px;">
              <div style="width:49%;">
                <div style="font-size:12px;margin-bottom:4px;">Number of leads you generate in a month</div>
                <div>
                <input v-model="formData.numberOfLeads" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="number">
                </div>
              </div>
              <div style="width: 49%; margin-left: 16px;">
                <div style="font-size:12px;margin-bottom:4px;">Total leads in your CRM</div>
                <div>
                <input v-model="formData.totalLeads" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="number">
                </div>
              </div>
            </div>
            <div style="display: flex; margin-top: 12px;">
              <div style="width:49%;">
                <div style="font-size:12px; margin-bottom:4px;">Which CRM do you use?</div>
                <div>
                <input v-model="formData.crmName" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="number">
                </div>
              </div>
              <div style="width: 49%; margin-left: 16px;">
                <div style="font-size:12px; margin-bottom:4px;">No of Agents?</div>
                <div>
                <input v-model="formData.agendaNumber" style="height: 26px; width: 100%; border: 1px solid #767477; border-radius: 4px;" type="number">
                </div>
              </div>
            </div>
            <div style="margin-top: 6px;">
              <div style="font-size: 14px;">What are your biggest lead sources?</div>
              <div style="display: flex;margin-left: 4px;">
                <div>
                  <input type="checkbox" id="source1" name="source1" @change="callLeadSource" value="Zillow">
                  <label for="vehicle1" style="font-size: 14px;"> Zillow</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="source2" name="source2" @change="callLeadSource" value="Realtor">
                  <label for="source2" style="font-size: 14px;"> Realtor</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="source3" name="source3" @change="callLeadSource" value="Ylopo">
                  <label for="source3" style="font-size: 14px;"> Ylopo</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="source4" name="source4" @change="callLeadSource" value="Others">
                  <label for="source4" style="font-size: 14px;"> Others</label>
                </div>
              </div>
            </div>
            <div style="margin-top: 10px;">
              <div style="font-size: 14px;">How did you hear about us?</div>
              <div style="display: flex;margin-left: 4px;">
                <div>
                  <input type="checkbox" id="about1" name="about1" @change="callHearAboutUs" value="Google">
                  <label for="about1" style="font-size: 14px;"> Google</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="about2" name="about2" @change="callHearAboutUs" value="Facebook">
                  <label for="about2" style="font-size: 14px;"> Facebook</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="about3" name="about3" @change="callHearAboutUs" value="Email">
                  <label for="about3" style="font-size: 14px;"> Email</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="about4" name="about4" @change="callHearAboutUs" value="Friends">
                  <label for="about4" style="font-size: 14px;"> Friends</label>
                </div>
                <div style="margin-left: 4px;">
                  <input type="checkbox" id="about5" name="about5" @change="callHearAboutUs" value="Real closers">
                  <label for="about5" style="font-size: 14px;"> Real closers</label>
                </div>
              </div>
            </div>
            <div @click="submitForm" class="submit-button">
              Submit
            </div>
          </div>
        </div>
      </div>
    </div>
  </transition>
</template>
<script>
import { ref, onMounted } from 'vue'
import BottomButton from './BottomButton.vue'
export default {
emits: ['esc-pressed', 'closeModal'],
components: {
  BottomButton
},
  props: {
    showCloseIcon: {
      type: Boolean,
      default: true
    },
    modalData: {
      type: Object,
      default: () => {}
    }
  },
  setup (props, { emit }) {
    const modal = ref(null)
    const formData = ref({
      name: '',
      emailId: '',
      phoneNumber: '',
      numberOfLeads: '-',
      totalLeads: '',
      crmName: '',
      agendaNumber: '',
      leadSource: [],
      hearAbout: []
    })
    onMounted(() => {
      modal.value.focus()
    })
    const callLeadSource = (event) => {
      if (formData.value.leadSource.includes(event.target.value)) {
        let index = formData.value.leadSource.indexOf(event.target.push)
        formData.value.leadSource.splice(index, 1)
      } else {
        formData.value.leadSource.push(event.target.value)
      }
    }
    const callHearAboutUs = (event) => {
      if (formData.value.hearAbout.includes(event.target.value)) {
        let index = formData.value.hearAbout.indexOf(event.target.value)
        formData.value.hearAbout.splice(index, 1)
      } else {
        formData.value.hearAbout.push(event.target.value)
      }
    }
    const submitForm = () => {
      alert(`name=${formData.value.name}, email id=${formData.value.emailId}, phone number=${formData.value.phoneNumber}
      number of leads=${formData.value.numberOfLeads}, total Leads=${formData.value.totalLeads}, CRM Name=${formData.value.crmName}, Agenda number=${formData.value.agendaNumber}, Lead Source: ${formData.value.leadSource.join(',')}, Hear About Us from ${formData.value.hearAbout.join(',')}`)
      callCloseModal()
    }
    const callCloseModal = () => {
      emit('closeModal')
        formData.value = {
        name: '',
        emailId: '',
        phoneNumber: '',
        numberOfLeads: '-',
        totalLeads: '',
        crmName: '',
        agendaNumber: '',
        leadSource: [],
        hearAbout: []
      }
    }
    return {
      modal,
      formData,
      callLeadSource,
      callHearAboutUs,
      submitForm,
      callCloseModal
    }
  }
}
</script>

<style lang="scss" scoped>
.modal-mask {
  position: fixed;
  z-index: 9998;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(45, 42, 46, 0.6);
  display: table;
  transition: opacity 0.3s ease;
}

.modal-wrapper {
  display: table-cell;
  vertical-align: middle;
}

.modal-container {
  position: relative;
  width: max-content;
  margin: 0px auto;
  padding: 16px 13px 14px 13px;
  background-color: white;
  box-shadow: 0px 2px 2px rgba(0, 0, 0, 0.08);
  transition: all 0.3s ease;
  box-sizing: border-box;
  width: 56%;

  .close-btn {
    position: absolute;
    right: 16px;
    top: 16px;
  }
}

.modal-header {
  color: #2D2A2E;
  text-align: center;
  box-sizing: border-box;
}

.modal-header h3 {
  font-size: 24px;
  line-height: 32px;
  letter-spacing: -0.02em;
  font-family: 'WorkSansBold';
}

.modal-header h6 {
  font-size: 15px;
  line-height: 22px;
  letter-spacing: -0.028em;
  margin-bottom: 20px;
  font-weight: normal;
}
.btn-circle-icon.close-btn img{
  height: 10px;
  width: 10px;
}

.modal-body {
  box-sizing: border-box;
  width: calc(100% - 20px);
  margin-top: 8px;
}

.modal-default-button {
  float: right;
}
.modal-enter-active {
  animation: bounce-in 1.5s;
}
.modal-leave-active {
  animation: bounce-in 1.5s reverse;
}
.submit-button {
  margin-top: 8px;
  width: 60px;
  height: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  background: #d95a00;
  color: white;
  &:hover {
    background: #fcd292;
    }
}
@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.25);
  }
  100% {
    transform: scale(1);
  }
}
input[type="checkbox"] {
  margin: 0px 2px 0px 0px;
}
</style>

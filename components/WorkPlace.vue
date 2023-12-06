<template>
  <li class="work-place">
    <h4 class="position">
      {{ position }}
    </h4>
    <div class="company">
      {{ company }}
    </div>
    <div class="place">
      <div class="place__work-time" :class="{ working: finishDate === -1 }">
        <span class="start">{{ startDate | moment('MMM YYYY') }}</span>
        <span class="separator"> - </span>
        <span v-if="finishDate !== -1" class="finish">{{ finishDate | moment('MMM YYYY') }}</span>
        <span v-else>present time</span>
        <span class="separator"> · </span>
        <span class="time">{{ workTime }}</span>
      </div>
    </div>
    <div class="desc">
      <slot />
    </div>
  </li>
</template>

<script>
import { ref } from 'vue'
import moment from 'moment'

export default {
  name: 'WorkPlace',
  props: {
    position: { type: String, required: true },
    company: { type: String, required: true },
    startDate: { type: Date, required: true },
    finishDate: { type: [Date, Number], required: false, default: -1 },
  },
  setup(props) {
    const workTime = ref('')
    const finDate = props.finishDate === -1 ? Date.now() : props.finishDate
    const startDate = moment(props.startDate)
    const finishDate = moment(finDate)
    const years = finishDate.diff(startDate, 'years')
    const months = (finishDate.diff(startDate, 'months') + 1) - years * 12

    workTime.value = (years > 0 ? years + ' years ' : '') + (months > 0 ? months + ' months' : '')

    return {
      workTime,
    }
  }
}
</script>

<style src="assets/styles/work-place.scss" lang="scss"></style>

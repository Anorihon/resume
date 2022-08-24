<template>
  <li>
    <h4 class="position">
      {{ position }}
    </h4>
    <div class="place">
      <div class="place__work-time" :class="{ working: finishDate === -1 }">
        <span class="start">{{ startDate | moment('MMM YYYY') }}</span>
        <span class="separator"> - </span>
        <span v-if="finishDate !== -1" class="finish">{{ finishDate | moment('MMM YYYY') }}</span>
        <span class="separator"> · </span>
        <span v-if="finishDate !== -1" class="time">{{ workTime }}</span>
      </div>
      <div class="place__separator">
        /
      </div>
      <div class="place__company">
        {{ company }}
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
    finishDate: { type: Date, required: false, default: -1 },
  },
  setup(props) {
    const workTime = ref('')

    if (props.finishDate !== -1) {
      const startDate = moment(props.startDate)
      const finishDate = moment(props.finishDate)
      const years = finishDate.diff(startDate, 'years')
      const months = finishDate.diff(startDate, 'months') + 1

      workTime.value = (years > 0 ? years + ' years' : '') + (months > 0 ? months + ' months' : '')
    }

    return {
      workTime,
    }
  }
}
</script>

<style lang="scss" scoped>
li {
  position: relative;
  padding-left: 25px;

  &:not(:first-child) {
    margin-top: 55px;
  }

  &::before {
    content: '';
    display: block;
    position: absolute;
    top: 0;
    left: -5px;
    width: 15px;
    height: 15px;
    background: #6a7bba;
    border-radius: 100%;
  }
}

.place {
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  gap: 20px;
  margin: 15px 0;

  font-size: 18px;
  color: #424243;

  &__work-time {
    font-size: 20px;
    font-weight: 600;
    color: #2c2c2c;
  }

  &__company {
    font-style: italic;
  }
}

.desc {
  color: #5b5b5c;
  line-height: 22px;
}
</style>

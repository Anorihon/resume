<template>
  <li class="skill">
    <div class="title">
      {{ title }}
    </div>
    <div class="progress-bar">
      <div class="fill-box" :style="{ width: progress + '%' }">
        <div class="content">
          {{ progress }}%
        </div>
      </div>
    </div>
  </li>
</template>

<script>
export default {
  name: 'SkillComponent',
  props: {
    title: { type: String, required: true },
    progress: { type: Number, required: true },
  }
}
</script>

<style src="assets/styles/skill.scss" lang="scss"></style>

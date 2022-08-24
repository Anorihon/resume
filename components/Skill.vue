<template>
  <li>
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

<style lang="scss" scoped>
.title {
  font-size: 18px;
  font-weight: 700;
  color: #262626;
  text-transform: uppercase;

  margin-bottom: 5px;
}

.progress-bar {
  position: relative;
  width: 100%;
  height: 11px;
  background: #3c3b3a;

  border-top: 1px solid #7f7c7c;
  border-right: 1px solid #5a5857;
  border-bottom: 1px solid #e6e5e4;
  border-left: 1px solid #5a5857;

  > .fill-box {
    position: absolute;
    top: 0;
    left: 0;
    width: 0;
    height: 100%;
    background: #6a7bba;
    transition: width .5s;

    border-top: 1px solid #a5add6;
    border-left: 1px solid #aeb5db;

    > .content {
      position: absolute;
      right: 0;
      bottom: 100%;
      padding: 5px;
      background: #6a7bba;

      border-top: 1px solid #a5add6;
      border-left: 1px solid #aeb5db;

      font-size: 14px;
      color: #ffffff;
    }
  }
}
</style>

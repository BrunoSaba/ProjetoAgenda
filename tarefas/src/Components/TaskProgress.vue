<template>
  <div class="task-progress">
      <span class="progress-value">{{ progress }}%</span>
      <div class="progress-bar" :style="{width: progress + '%'}"></div>
  </div>
</template>

<script>
export default {
    props: {
        progress: { type: Number, default: 0 }
    }
}
</script>

<style>
    .task-progress {
        position: relative;
        width: 80%;
        border: 1px solid #ffffff;
        color:#ffffff;
        border-radius: 8px;
        margin-bottom: 15px;
        display: flex;
        flex-direction: column;
        align-items: center;
    }
    .progress-bar{
        position: absolute;
        border-radius: 8px;
        height: 100%;
        background-color: greenyellow;
    }
    .progress-value{
        z-index: 2;
        color: black;
    }
</style>
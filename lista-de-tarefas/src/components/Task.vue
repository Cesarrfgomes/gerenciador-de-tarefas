<script setup>
const props = defineProps({
  task: Object,
});
</script>

<template>
  <div class="container-task">
    <div class="content-task">
      <span>{{ props.task.title }}</span>
      <div class="actions">
        <img src="../assets/edit.svg" alt="edit" />
        <img src="../assets/delete.svg" alt="delete" />
      </div>
    </div>
    <hr />
  </div>
</template>

<style scoped lang="scss">
.container-tasks {
  display: flex;
  flex-direction: column;
  width: 746px;

  hr {
    margin: 16px 0;
  }
}

.content-task {
  display: flex;
  justify-content: space-between;

  width: 746px;

  span {
    font-family: "Mulish";
    font-style: normal;
    font-weight: 700;
    font-size: 18px;
    line-height: 23px;
    display: flex;
    align-items: center;
    color: #484545;
  }
}

.actions {
  display: flex;
  gap: 8px;

  img {
    width: 24px;
    height: 24px;
    cursor: pointer;
    &:hover {
      opacity: 0.9;
    }
  }
}
</style>

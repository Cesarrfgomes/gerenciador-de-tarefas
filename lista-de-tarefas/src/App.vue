<script setup>
import Task from "./components/Task.vue";
import { ref } from "vue";

const taskTitleInput = ref("");
const allTasks = ref([]);

const addNewTask = () => {
  if (!taskTitleInput.value) {
    return;
  }

  const localAllTasks = [...allTasks.value];

  localAllTasks.push({
    id: crypto.randomUUID(),
    title: taskTitleInput.value,
  });

  allTasks.value = [...localAllTasks];
  taskTitleInput.value = "";
};
</script>

<template>
  <div class="container">
    <header>
      <img src="./assets/logo.svg" alt="logo" />
    </header>

    <main>
      <div class="insert-task">
        <input
          type="text"
          placeholder="Inserir nova tarefa"
          v-model="taskTitleInput"
        />
        <button @click="addNewTask()">Adicionar</button>
      </div>
      <div class="tasks-list">
        <div v-for="task in allTasks" :key="task.id">
          <Task :task="task" />
        </div>
      </div>
    </main>
  </div>
</template>

<style scoped lang="scss">
.container {
  display: flex;
  flex-direction: column;
  align-items: center;

  width: 100vw;
  height: 100vh;
}

header {
  display: flex;
  align-items: center;
  justify-content: center;

  width: 100%;
  padding: 24px 0;

  igm {
    width: 449px;
    height: 94px;
  }
}

main {
  width: 924px;
  height: 448px;
}

.insert-task {
  display: flex;
  gap: 16px;

  input {
    width: 100%;
    height: 48px;
    border: none;
    padding: 16px;
    background: #ffffff;
    border-radius: 10px;
  }

  button {
    width: 167px;
    height: 48px;
    border: none;
    border-radius: 10px;

    background: #41af1a;
    color: #ffffff;
    cursor: pointer;

    &hover {
      opacity: 0.9;
    }
  }
}

.tasks-list {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 924px;
  height: 555px;
  margin: 24px 0 95px 0;
  padding: 50px 89px;

  background: #fffafa;
  border-radius: 24px;
}
</style>

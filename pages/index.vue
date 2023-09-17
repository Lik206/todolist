<template>
  <div>
    <div id="navbar">
      <b-navbar variant="secondary" type="light">
        <b-navbar-brand tag="h1" class="mb-0 font-weight-bold text-light"
          >ToDoList</b-navbar-brand
        >
      </b-navbar>
    </div>
    <div id="heading" class="container">
      <b-navbar class="border-bottom border-secondary">
        <b-navbar variant="light" type="light">
          <b-navbar-brand tag="h1" class="mt-5 mb-0 font-weight-bold">
            Task
          </b-navbar-brand>
        </b-navbar>
        <b-navbar class="ml-auto">
          <button class="btn btn-secondary mt-5" @click="inputDisplay">Add</button>
        </b-navbar>
      </b-navbar>
    </div>

    <div id="content" class="mt-5">
      <div class="row justify-content-around justify-content-sm-center">
        <div
          v-for="(item, index) of updateTask"
          :key="index"
          style="width: 18rem"
          class="col-12 col-sm-9 col-md-6 col-lg-4 ml-3 mt-4"
        >
          <div
            class="card-body card d-flex flex-row bd-highlight mb-3 bg-secondary text-light"
          >
            <div class="mr-2"><input class="p-5" type="checkbox" /></div>
            <div class="col-12">
              <h5 class="font-weight-bolder">{{ item.task }}</h5>
              <h2 class="border border-light border-2 opacity-50"></h2>
              <p class="card-text">
                {{ item.detail }}
              </p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <div id="input" class="container-fluid mt-5">
      <div class="d-flex justify-content-center">
        <form
          v-if="display"
          class="border border-5 border-secondary rounded p-4 col-12 col-sm-9 col-md-5 col-lg-4 ml-3 mt-4"
          @submit.prevent="addTask"
        >
          <h5 class="text-center font-weight-bolder">Add Task</h5>
          <input
            id="task"
            v-model="task"
            value="jel"
            class="form-control border border-2 border-secondary"
            type="text"
            name="task"
            placeholder="Input title task"
          />
          <textarea
            id="detailTask"
            v-model="detail"
            class="form-control border border-2 border-secondary mt-3"
            name="detail"
            cols="20"
            rows="5"
            style="resize: none"
            placeholder="Input description"
            @keyup.enter="addTask"
          ></textarea>
          <div class="d-flex justify-content-around mt-4">
            <button class="btn btn-secondary" type="submit">Submit</button>
            <button class="btn btn-secondary" @click="cancelTask">Cancel</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',
  data() {
    return {
      display: false,
      task: '',
      detail: '',
      updateTask: [],
    }
  },
  methods: {
    inputDisplay() {
      this.display = true
    },
    cancelTask() {
      this.display = false
    },
    addTask() {
      if (this.task !== '' && this.detail !== '') {
        const item = {
          form: {
            task: this.task,
            detail: this.detail,
          },
        }

        this.updateTask.push(item.form)
        this.task = '' // Reset the input value
        this.detail = '' // Reset the input value
      }
    },
  },
}
</script>

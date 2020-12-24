<template>
  <div class="container">
    <div class="row">
      <h3>Nuxt todo app</h3>
      <div class="col-12">
        <b-form-group
            label="タイトル:"
        >
          <b-form-input
              placeholder="todoリストに追加するタイトルを入力してください"
              required
              type="text"
              v-model="add_todo"
              :state="addTodoState"
          ></b-form-input>
        </b-form-group>
        <b-button block @click="addButton">追加する</b-button>
        <hr>
      </div>

      <div :key="todo.id" class="col-12" v-for="todo in todos">

        <b-form-checkbox
            name="タイトル"
            v-model="todo.done"
        >
          {{ todo.title }}
        </b-form-checkbox>

        <hr>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      todos: [
        {
          id: 1,
          title: '勤怠システムを進める',
          done: false
        }
      ],

      add_todo: ''
    }
  },
  methods: {
    addButton: function () {
      if(this.add_todo.length === 0){
        alert('最低でもタイトルは1文字以上入力してください。')
        return
      }

      const now_max_id = this.todos.reduce((a,b)=>{
        return a.id > b.id ? a : b
      })

      this.todos.unshift({
        id: Number(now_max_id.id) + 1,
        title: this.add_todo,
        done: false,
      })

      this.add_todo = ''
    }
  },
  computed:{
    addTodoState: function (){
      if(this.add_todo.length > 0){
        return true
      }else {
        return false
      }
    }
  }

}
</script>

<style>

</style>

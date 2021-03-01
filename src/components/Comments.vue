<template>
  <div>
  <FormTodo
    @add-todo="addComment"
  >

  </FormTodo>
  <v-container>
    <v-data-table
   :headers="headers"
    :items="comment"
    class="elevation-1"
  >
    <template #[`item.name`]="{value}">
      {{value}}
    </template>
    <template #[`item.comment`]="{value}">
      {{value}}
    </template >
    <template #[`item.action`]="{item }">
      <v-icon
        small
        class="mr-2"
        @click="deleteItem(item)"
      >
       mdi-delete
      </v-icon>
    </template>
  </v-data-table>
  </v-container>
  </div>
</template>

<script>
  import FormTodo from './FormTodo'
  export default {
    name: 'HelloWorld',

    components: {
      FormTodo,
    },
    data() {
      return{
        headers: [
          {
            text: 'name',
            align: 'start',
            sortable: false,
            value: 'name',
          },
          { text: 'comment', value: 'comment' },
          { text: 'action', value: 'action' },
        ],
        comment: [
          
        ],
      }
    },
    methods: {
      addComment(comments){
        console.log(comments);
        this.comment.push(comments);
      },
      deleteItem(item){
        this.comment.splice(item, 1);
      }
    },
  }
</script>

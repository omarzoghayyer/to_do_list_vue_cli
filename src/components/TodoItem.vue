<template>
    <div class="todo-item" v-bind:class="{'is-complete':todo.completed}">
        <p> 
            <input type="checkbox" v-on:change="markComplete">   
            {{todo.title}}
            <button  @click="$emit('del-todo', todo.id)"   class="del">X</button>
        </p>
    </div>
</template>

<script>
export default {
    name: 'TodoItem',
    props: ['todo'],
    methods: {
        markComplete() {
            this.todo.completed = !this.todo.completed;
        }
    }
}
</script>



<style scoped>

/*styleing the todo items. */

.todo-item {
    background: rgb(243, 242, 242);
    padding: 10px;
    border-bottom: 1px rgb(112, 9, 9) dotted;
}
.is-complete {
    text-decoration: line-through;
}
.del {
    background: rgb(0, 60, 255);
    color: white;
    border: none;
    padding: 5px 9px;
    border-radius: 50%;
    cursor: pointer;
    float: right;
}


</style>
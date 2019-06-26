<template>
    <div>
        <transition-group tag="ul" name="todo">
        <ul>
            <li v-for="(todoItem, index) in todolist">
            <span>  {{ todoItem }}</span>
            <button v-on:click="removeTodoItem(todoItem, index)">remove</button>
            </li>
        </ul>
        </transition-group>
    </div>
</template>

<script>
export default {
    props: ['todolist'],//props 속성에다가 데이터를 내려주기만 하면된다?
    
    //App.vue에서 props로 바로 쓰기 때문에 data가 필요없어
    // data() {
    //     return {
    //         todoItems: []
    //     }
    // },

    methods: {
        // fetchTodoItems: function() {
        //     for (var i =0; i < localStorage.length; i++){
        //         var item = localStorage.key(i);
        //         this.todoItems.push(item);            
        //     }
        // },
        removeTodoItem: function(todo, index) {
            console.log('deleted', todo, index);
            
            this.$emit('remove', todo, index);

            //localStorage.removeItem(todo);
        },
        //서버의 데이터 불러오기
        //axios.get();
    }, 

    // 컴포넌트가 생성되자마자 실행되는 로직. 객체지향에서 생성자같은거인듯
    // created: function() {
    //     this.fetchTodoItems();
    // },
};
</script>

<style>

</style>

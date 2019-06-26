<template>
    <div>
        <input 
        type="text" 
        v-model="inputText"
        v-on:keyup.enter="addTodo">
        <button v-on:click="addTodo">add</button>
    </div>
</template>

<script>
export default {
    data() {
        return {
            inputText: '',
        };
    },
    methods:{
        addTodo: function() {
            var value = this.inputText;
            this.$emit('add', value);//add라는 주석과 함께 입력된 값을 하위 컴포넌트에서 상위 컴포넌트로 보낸다.
            //localStorage.setItem(value, value);
            this.clearinput();
        },
        clearinput: function(){
            this.inputText = "";
        },
    }
}
</script>

<style>

</style>

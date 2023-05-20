<template>
    <div class="inputBox shadow">
        <!-- 화면에 입력된 값을 저장하여 서버에 보냄 / watch와 같은 고급 속성 이용 → 추가로직 수행 -->
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do"
        v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="addBtn fa fa-plus" aria-hidden="true"></i>
        </span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ''
        }
    },
    methods: {
        addTodo() {
            // console.log(this.newTodoItem);
            // exception 예외 처리 
            if (this.newTodoItem !== "") {
                let value = this.newTodoItem && this.newTodoItem.trim();
                localStorage.setItem(value, value);
                this.clearInput();
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    }
}
</script>

<style>
input:focus{
    outline: none;
}
.inputBox{
    background: white;
    height: 50px;
    line-height: 50px;
    border-radius: 5px;
}
.inputBox input{
    border-style: none;
    font-size: 0.9rem;
}
.addContainer{
    float: right;
    background: linear-gradient(to right,#6478FB,#8763FB);
    display: inline-block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
}
.addBtn{
    color: white;
    vertical-align: middle;
}
</style>
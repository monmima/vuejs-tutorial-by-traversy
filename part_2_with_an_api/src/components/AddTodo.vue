<template>
    <div>
        <form @submit="addTodo">
            <input type="text" v-model="title" name="title" placeholder="Add Todo...">
            <input type="submit" value="Submit" class="btn">
        </form>
    </div>
</template>

<script>
// import uuid from "uuid"; // no longer needed in part 2 (deleted at 54:47)

export default {
    name: "AddTodo",
    data() {
        return {
            title: ""
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();

            const newTodo = {
                // temporary solution below; this part of the tutorial doesn't seem to work
                // id: uuid.v4(),
                // id: 6, // this line is no longer needed in part 2 (delete at 55.47)
                title: this.title,
                completed: false
            }
            // send up to parent
            this.$emit("add-todo", newTodo);

            // to clear the input bar
            this.title = "";
        }
    }
}
</script>

<style scoped>
    form {
        display: flex;
    }

    input[type="text"] {
        flex: 10;
        padding: 5px;
    }

    input[type="submit"] {
        flex: 2;
    }
</style>
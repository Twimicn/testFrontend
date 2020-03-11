<template>
    <div class="hello">
        <h1>{{ msg }}</h1>
        <table class="test-table">
            <tr>
                <td>ID</td>
                <td>Username</td>
            </tr>
            <tr v-for="(user,index) in users" v-bind:key="index">
                <td>{{ user.id }}</td>
                <td>{{ user.username }}</td>
            </tr>
        </table>
    </div>
</template>
<script>
    export default {
        name: 'HelloWorld',
        props: {
            msg: String,
            users: Array,
        },
        created() {
            fetch('http://localhost:8080/users').then(r => r.json()).then(r => {
                this.users = r;
            })
        },
    }
</script>
<style scoped>
    .test-table {
        border: 1px solid #2c3e50;
        width: 100%;
    }

    .test-table td {
        padding: 5px 10px;
        border: 1px solid greenyellow;
    }
</style>

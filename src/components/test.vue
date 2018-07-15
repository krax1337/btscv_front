<template>
    <div class="test">
        <ul v-if="users.lentgh > 0">
            <li v-for="(index,user) of users" :key = "index">
                <h1> {{ user.email }}</h1>
                <h1>{{ user.password_digest }}</h1>
                
            </li>
        </ul>
        <!-- <h1>{{title}}</h1> -->
    </div>

</template>

<script>
import axios from 'axios';

export default {
    name: 'test',
    data() {
        return {
            users: [],
            errors: [],
            title: 'Hello world!'
        }
    },
    
    created() {
            axios.get("https://btscv.herokuapp.com/api/v1/index")
            .then(response => {
                console.log(response.data)
                // this.users["Access-Control-Allow-Origin"] = 'https://btscv.herokuapp.com/api/v1/index'
                // this.users["Access-Control-Request-Method"] = '*'
                this.users = response.data
            })
            .catch(e => {
                this.errors.push(e)
            })
        
    }
}
</script>

<style scoped>

</style>

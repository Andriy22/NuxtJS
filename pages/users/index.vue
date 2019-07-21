<template>
    <section>
        <h1>Users page</h1>

        <ul>
            <li v-for="user of users" :key="user.id">
             <a href="#" @click.prevent="openUser(user.id)"> User {{user.name}} </a> 
            </li>
        </ul>
    </section>
</template>


<script>
export default {

    async fetch({store}) {
        if (store.getters['users/users'].length === 0) {
            await store.dispatch('users/fetch');
        }
    },
    computed: {
        users() {
            return this.$store.getters['users/users'];
        }
    },
    // OLD CODE
    // async asyncData({$axios}) {
    //     const users = await $axios.$get('https://jsonplaceholder.typicode.com/users');
    //     return {users};
    // },
    // data: () => ({
    //     users: [],
    // }),
    // async mounted() {
    //     this.users = await this.$axios.$get('https://jsonplaceholder.typicode.com/users');
    // },
    methods: {
        openUser(user) {
            this.$router.push('/users/' + user);
        }
    }
}
</script>

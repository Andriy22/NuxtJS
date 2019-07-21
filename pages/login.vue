<template>
    <section>
        <div  v-if="$route.query.message" class="alert alert-danger">
            Need login first
        </div>
        <form @submit.prevent="onSubmit">
            <h1>Login page</h1>
            <div class="form-group">
                <input type="text" class="form-control"/>
            </div>
            <p>
                <nuxt-link to="/">Go to home</nuxt-link>
            </p>
           

            <button class="btn btn-primary" type="submit">Sign In</button>
        </form>
    </section>
</template>

<script>
export default {
    layout: 'empty',
    methods: {
        onSubmit() {
            this.$store.dispatch('login');
            this.$router.push('/');
        }
    }
}
</script>


<style scoped>
 form{
     width: 400px;
     margin: 0 auto;
 }
</style>

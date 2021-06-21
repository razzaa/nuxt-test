<template>
    <div class="admin-new-post-page">
        <section class="new-post-form">
            <AdminPostForm @submit="onSubmitted"/>
        </section>
    </div>
</template>

<script>
import axios from 'axios'
import AdminPostForm from '@/components/Admin/AdminPostForm'
export default {
    layout: 'admin',
    middleware: ['check-auth', 'auth'],
    components: {
        AdminPostForm,
    },
    methods: {
        onSubmitted(postData) {
            this.$store.dispatch("addPost", postData).then(() => {
                this.$router.push("/admin");
            });
        }
    }
}
</script>
<style scoped>
.admin-new-post-page {
    width: 60%;
    margin: auto;
}
</style>
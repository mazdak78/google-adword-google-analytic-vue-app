<template>

</template>

<script>
    export default {
        name: "googleAnalytic",
        mounted(){

            // just set a title and page
            var title =  window.location.pathname;
            var page = location.href;

            //ID from Google Analytic tracking code
            gtag('config', 'UA-XXXXXXXX-X', {
                'page_title' : page,
                'page_path': title
            });
        }
    }
</script>

<style scoped>

</style>

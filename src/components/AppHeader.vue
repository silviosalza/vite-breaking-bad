<script>
export default{
    name: "AppHeader",
    props: {
        title: String
    }
}

</script>

<template>
    <header>
        <div class="container text-center">
            <h1>{{title}}</h1>
        </div>

    </header>
</template>

<style scoped lang="scss">
header{
    height: 100px;
    background-color: rgb(255, 241, 215);
 }


</style>
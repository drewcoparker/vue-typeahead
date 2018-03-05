<template>
    <div id="app">
        <Typeahead/>
    </div>
</template>

<script>
import Typeahead from './components/Typeahead'

export default {
    name: 'App',
    components: {
        Typeahead
    }
}
</script>

<style>
body {
    margin: 0; padding: 0;
    font-family: 'Open Sans', Arial, sans-serif;
    box-sizing: border-box;
    background: linear-gradient(135deg, #41B883 0%,#354953 100%);
    background-size: cover;
    min-height: 100vh;
    color: #fff;
}
#app {
    font-family: 'Muli', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
    max-width: 900px;
    margin: 60px auto;
}
</style>

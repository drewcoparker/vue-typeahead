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
#app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>

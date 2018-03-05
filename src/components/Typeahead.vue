<template>
    <div>
        <input
            v-model="query"
            type="text"
            class="search-input"
            :placeholder="placeHolder"
        />

        <transition-group name="fade" tag="ul" class="results">
            <li v-for="item in filtered" :key="item">
                <span>
                    <strong>{{ item.title }}</strong> - <small>{{ item.id }}</small><br>
                    <small>{{ item.body }}</small>
                </span>
            </li>
        </transition-group>

        <p v-show="isEmpty">No result</p>
    </div>
</template>

<script>
export default {
    name: 'Typeahead',

    props: {
        source: {
            type: [String, Array],
            required: true
        },
        filterKey: {
            type: String,
            required: true
        },
        startAt: {
            type: Number,
            default: 3
        },
        placeHolder: {
            type: String,
            default: ''
        }
    },

    data () {
        return {
            items: [],
            query: ''
        }
    },

    methods: {
        fetchItems () {
            if (typeof this.source === 'string') {
                fetch(this.source)
                    .then(res => res.json())
                    .then(data => this.items = data)
                    .catch(err => console.error(err))
            } else {
                this.items = this.source
            }
        }
    },

    computed: {
        filtered () {
            if (this.query.length >= this.startAt) {
                return this.items.filter(item => {
                    if (item.hasOwnProperty(this.filterKey)) {
                        return item[this.filterKey]
                            .toLowerCase()
                            .indexOf(this.query.toLowerCase()) > -1
                    } else {
                        console.log(`This object doesn't have a ${this.filterKey} property.`)
                    }
                })
            }
        },

        isEmpty () {
            if (typeof this.filtered === 'undefined') {
                return false
            } else {
                return this.filtered.length < 1
            }
        }
    },

    mounted () {
        console.log('mounting comp')
        this.fetchItems()
    }

}
</script>

<style>
.search-input {
    width: 100%;
    padding: 1.5em 1em;
    font-size: 1em;
    outline: 0;
    border: 5px solid #41B883;
}

.results {
    margin: 0;
    padding: 0;
    text-align: left;
    position: relative;
}

.results li {
    background: rgba(53, 73, 94, 0.3);
    margin: 0;
    padding: 1em;
    list-style: none;
    width: 100%;
    border-bottom: 1px solid #394E62;
    transition: ease-in-out 0.5s;
}

.fade-enter-active, .fade-leave-active {
    transition: opacity 0.3s;
}

.fade-enter, .fade-leave-to {
    opacity: 0;
}
</style>

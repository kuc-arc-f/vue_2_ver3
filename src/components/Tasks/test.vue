<template>
    <div>
        <h1>tasks- test:</h1>
        <hr />
        test : {{ message }}
    </div>
</template>

<script>
import {Mixin} from '../../mixin'

export default {
    mixins:[Mixin],
    created() {
        console.log( 'test_func='+ this.test_func() )
    },
    data() {
        return {
            user : [],
            message :''
        }
    },
    methods: {
    }
}
</script>


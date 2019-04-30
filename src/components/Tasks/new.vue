<template lang="html">
    <div class="container">
            <div class="form-group">
                <label for="TopicTitle">タイトル</label>
                <input type="text" class="form-control" id="title" v-model="title">
            </div>
            <div class="form-group">
                <label for="TopicContent">content</label>
                <textarea class="form-control" id="content" rows="3" v-model="content"></textarea>
            </div>
            <button v-on:click="createTask">投稿</button>
    </div>
</template>

<script>
import firebase from 'firebase'
var tableName = 'tasks'
import {Mixin} from '../../mixin'

export default {
    mixins:[Mixin],
    created() {
        this.database = firebase.firestore()
        this.check_userState(this.sysConst.STORAGE_KEY_userData, this)
        this.user_id = this.get_userId(this.sysConst.STORAGE_KEY_userData )
        /* console.log( 'new.uid ='+ this.user_id )  */
    },
    data() {
        return {
            title:'',
            content:'',
            user_id: '',
        }
    },
    methods: {
        createTask: function() {
            console.log('#create')
            var self = this
            if (this.newTodoName == "") { return; }
            this.database.collection(tableName).add({
                title: this.title,
                content: this.content,
                uid : this.user_id,
                up_date: new Date()
            }).then(function(docRef) {
                console.log("Document written with ID: ", docRef.id)
                self.$router.push('/tasks')
            }).catch(function(error) {
                console.log("Error adding document: ", error)
            })
            this.newTodoName = ""
        },
    }
}
</script>

<template lang="html">
    <div class="container">
            <div class="form-group">
                <label for="emailTitle">email</label>
                <input type="text" class="form-control" id="email" v-model="email">
            </div>
            <div class="form-group">
                <label for="passwordTitle">password</label>
                <input type="text" class="form-control" id="password" v-model="password">
            </div>
            <button v-on:click="procLogin">Login</button>
    </div>
</template>

<script>
import firebase from 'firebase'
import {Mixin} from '../../mixin'
//
export default {
    mixins:[Mixin],
    created() {
        this.database = firebase.firestore()
        this.check_userState(this.sysConst.STORAGE_KEY_userData, this)
//        var d = this.get_exStorage(this.sysConst.STORAGE_KEY_userData)
    },
    data() {
        return {
            email : '',
            password : '',
        }
    },
    methods: {
        procLogin: function() {
            firebase.auth().signInWithEmailAndPassword(this.email, this.password).catch(function(error) {
                console.log("#handle-start");  
                var errorCode = error.code;
                var errorMessage = error.message;
                if (errorCode === 'auth/wrong-password') {
                    /* alert('Wrong password.') */
                    console.log('Wrong password.');
                } else {
                    console.log(errorCode);
                    console.log(errorMessage);
                }
                console.log(error);
                alert("#Login-error");
            })
            var self = this
            var log = function(){
                var user = firebase.auth().currentUser;
                var email=null;
                if (user != null) {
                    email = user.email;
                    if(email != null){
                        console.log(email)
                        console.log(user.uid )
                        var param = [{'uid': user.uid }]
                        self.set_exStorage(self.sysConst.STORAGE_KEY_userData, param )
                        self.$router.push('/')
                    }
                }else{
                    console.log('#user=NULL');
                }
            }
            setTimeout(log, 2000);
        },
    }
}
</script>

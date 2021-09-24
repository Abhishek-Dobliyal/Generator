<template>
  <Header heading="Password Generator" subHeading="Generates password as per requirements" color="slategrey" borderColor="secondary"></Header>
  <div class="container mt-2 text-center">
    <div class="container input-group mt-4 pt-3 w-50">
        <span class="input-group-text">Length</span>
        <input v-model="passLen" type="text" placeholder="Password Length" class="form-control" aria-describedby="inputGroup-sizing-sm" id="passwordLen">
    </div>
    <div class="container d-flex justify-content-center mt-4 bg-dark text-light">
        <div class="container p-3">
            <div class="form-check form-switch">
                <input v-model="useLowercase" class="form-check-input" type="checkbox" id="flexSwitchCheckDefault" disabled>
                <label class="form-check-label" for="flexSwitchCheckDefault">Include Lowercase</label>
            </div>
            <div class="form-check form-switch">
                <input v-model="useUppercase" class="form-check-input" type="checkbox" id="flexSwitchCheckChecked">
                <label class="form-check-label" for="flexSwitchCheckChecked">Include Uppercase</label>
            </div>
        </div>
        <div class="container p-3">
            <div class="form-check form-switch">
                <input v-model="useNumerics" class="form-check-input" type="checkbox" id="flexSwitchCheckDisabled">
                <label class="form-check-label" for="flexSwitchCheckDisabled">Include Numerics</label>
            </div>
            <div class="form-check form-switch">
                <input v-model="useSpecial" class="form-check-input" type="checkbox" id="flexSwitchCheckCheckedDisabled">
                <label class="form-check-label" for="flexSwitchCheckCheckedDisabled">Include Special</label>
            </div>
        </div>
    </div>
    <div class="container w-100 input-group mt-5 pt-4">
        <span class="input-group-text">Password</span>
        <input v-model="password" type="text" class="form-control w-50" disabled>
    </div>
    <button class="btn btn-outline-secondary mt-5" @click="generate">Generate Password</button>
  </div>
</template>

<script>
import Header from  '../components/Header.vue'
export default {
    name: 'Password',
    components: {
        Header
    },
    data() {
        return {
            passLen: 8,
            useLowercase: true,
            useUppercase: false,
            useNumerics: false,
            useSpecial: false,
            password: ''
        }
    },
    methods: {
        generatePassword(len) {
            const charSet = {
                lower: 'abcdefghijklmnopqrstuvwxyz',
                upper: 'ABCDEFGHIJKLMNOPQRSTUVWXYZ',
                numbers: '0123456789',
                special: '!@#$%^&*();:><./?' 
            }

            let password = ''
            for (let i=0; password.length < len; i++){
                if (this.useLowercase) {
                    password += charSet.lower.charAt(Math.floor(Math.random() * charSet.lower.length))
                } if (this.useUppercase) {
                    password += charSet.upper.charAt(Math.floor(Math.random() * charSet.upper.length))
                } if (this.useNumerics) {
                    password += charSet.numbers.charAt(Math.floor(Math.random() * charSet.numbers.length))
                } if (this.useSpecial) {
                    password += charSet.special.charAt(Math.floor(Math.random() * charSet.special.length))
                }
            }

            return password;
        },
        generate() {
            if (this.passLen < 8) {
                this.passLen = 8;
            } else if (this.passLen > 16){
                 this.passLen = 16;
            } else  {
                this.password = this.generatePassword(this.passLen);
                console.log(this.passLen, this.password);
            }
        }
    }
}
</script>

<style>

</style>
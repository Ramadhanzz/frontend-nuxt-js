<template>
    <v-row>
        <v-col cols="10" offset="1" md="4" offset-md="4">
            <v-card>
                <v-toolbar dark color="primary">Register</v-toolbar>
                <v-card-text>
                    <v-form>
                        <v-text-field type="text" label="Name" required :rules="rules.fullname" v-model="form.fullname" />
                        <v-text-field type="email" label="Email" required :rules="rules.email" v-model="form.email"/>
                        <v-text-field type="password" label="Password" required :rules="rules.password" v-model="form.password"/>
                        <v-text-field label="Konfirmasi Password" type="password" required :rules="rules.password_confirmation" v-model="form.password_confirmation"/>
                    </v-form>
                </v-card-text>

                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="primary" @click="fetchSomething">Register</v-btn>
                </v-card-actions>
            </v-card>
            <!-- Silahkan Login -->
            <div class="d-flex align-baseline">
                <p>Kamu sudah punya akun?</p>
                <v-btn text plain to="/auth/login" :ripple="false" class="pl-1" color="primary">Login</v-btn>
            </div>
        </v-col>
    </v-row>
</template>

<script>
export default {
    layout: 'auth',
    data() {
        return {
            // Form Model
            form: {
                fullname: '',
                email: '',
                password: '',
                password_confirmation: '',
            },
            rules: {
                fullname: [
                    (v) => !!v || 'Fullname is required'
                ],
                email: [
                    (v) => !!v || 'E-mail is required',
                    (v) => /.+@.+/.test(v) || 'E-mail must be valid',
                ],
                password: [
                    (v) => !!v || 'Password is required',
                    (v) => v.length >= 6 || 'Password must be at least 6 Characters',
                ],
                password_confirmation: [
                    (v) => !!v || 'Password Confirmation is required',
                    (v) => v === this.form.password || 'Password Confirmation must be same with password',
                ]
            }
            
        }
    },
    methods: {
        async onSubmit() {
            this.$axios.$post('https://webhook.site/d00743cb-374f-4079-be76-71a433b462ed', this.form)
                .then((res) => {
                    console.log('Berhasil');
                })
                .catch((err) => {
                    console.log('Error');
                })
        },

        async fetchSomething() {
            const ip = await this.$axios.$get('http://icanhazip.com')
            console.log(ip);
        }
    }
}
</script>

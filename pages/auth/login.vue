<template>
    <v-row>
        <v-col cols="10" offset="1" md="4" offset-md="4">
            <v-card>
                <v-toolbar dark color="primary">Login</v-toolbar>
                <v-card-text>
                    <v-form>
                        <v-text-field type="email" label="Email" required />
                        <v-text-field type="password" label="Password" required />
                    </v-form>
                </v-card-text>

                <v-card-actions>
                    <v-spacer></v-spacer>
                    <v-btn color="primary">Login</v-btn>
                </v-card-actions>
            </v-card>
            <!-- Silahkan Login -->
            <div class="d-flex align-baseline">
                <p>Kamu belum punya akun?</p>
                <v-btn text plain to="/auth/register" :ripple="false" class="pl-1" color="primary">Register</v-btn>
            </div>
        </v-col>
    </v-row>
</template>

<script>
export default {
    layout: 'auth',
}
</script>

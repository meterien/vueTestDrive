<template>
    <div>
        <v-card class="ma-3 pa-2">
            <v-card-title>{{ title }}</v-card-title>
            <v-card-text>
                <v-form v-model="valid" ref="form1">
                    <v-text-field
                        v-model="name"
                        :rules="nameRules"
                        :counter="25"
                        label="Prénom"
                        required
                    ></v-text-field>
                    <v-text-field
                        v-model="surname"
                        :rules="surnameRules"
                        :counter="25"
                        label="Nom"
                        required
                    ></v-text-field>
                    <v-menu
                        ref="menu"
                        :close-on-content-click="false"
                        v-model="menu"
                        :nudge-right="40"
                        lazy
                        transition="scale-transition"
                        offset-y
                        full-width
                        min-width="290px"
                    >
                        <v-text-field
                        slot="activator"
                        v-model="date"
                        label="Date de naissance"
                        prepend-icon="event"
                        readonly
                        ></v-text-field>
                        <v-date-picker
                        ref="picker"
                        v-model="date"
                        :max="new Date().toISOString().substr(0, 10)"
                        min="1950-01-01"
                        @change="save"
                        ></v-date-picker>
                    </v-menu>
                    <v-text-field
                        v-model="email"
                        :rules="emailRules"
                        label="Courriel"
                        required
                    ></v-text-field>
                    <v-btn
                        :disabled="!valid"
                        @click="dialog = true"
                    >
                    Soumettre
                    </v-btn>
                    <v-btn @click="clear">Effacer le formulaire</v-btn>
                    <v-dialog
                        v-model="dialog"
                        hide-overlay
                        persistent
                        width="300"
                    >
                        <v-card
                            color="primary"
                            dark
                        >
                            <v-card-title></v-card-title>
                            <v-card-text>
                            Chopping somes carots...
                            <v-progress-linear
                                indeterminate
                                color="white"
                                class="mb-0"
                            ></v-progress-linear>
                            </v-card-text>
                        </v-card>
                    </v-dialog>
                </v-form>
            </v-card-text>
       </v-card>
    </div>
</template>

<script>
export default {
    data: function() {
        return {
            title: 'Formulaire #1',
            valid: true,
            name: '',
            date: null,
            menu: false,
            dialog: false,
            nameRules: [
                v => !!v || 'Name is required',
                v => (v && v.length <= 10) || 'Name must be less than 10 characters'
            ],
            email: '',
            emailRules: [
                v => !!v || 'E-mail is required',
                v => /.+@.+/.test(v) || 'E-mail must be valid'
            ],
        }
    },
    watch: {
        menu: function(val) {
            val && this.$nextTick(() => (this.$refs.picker.activePicker = 'YEAR'))
        },
        dialog: function(val) {
            if (!val) return
            setTimeout(() => (this.dialog = false), 4000)
        }
    },
    methods: {
        clear: function() {
            this.$refs.form1.reset()
        },
        save: function(date) {
            this.$refs.menu.save(date)
        }
    }
}
</script>

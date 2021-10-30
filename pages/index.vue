<template>
    <div id="index">
        <section>
            <b-container>
                <h2>Case Anything</h2>
                <h4>Quick online casing tool to convert your JSON or DTOs</h4>
                <br />
                <b-form @submit.stop.prevent="onSubmit">
                    <b-row>
                        <b-col sm="6"
                            ><div>
                                <b-form-textarea v-model="form.input" id="textarea" placeholder="Paste your object here..." rows="10" max-rows="10"></b-form-textarea>
                                <b-form-invalid-feedback id="input-live-feedback"> Please provide data </b-form-invalid-feedback>
                                <br />
                                <div>
                                    <b-form-select v-model="form.inputSelection" :options="options"></b-form-select>
                                </div></div
                        ></b-col>
                        <b-col sm="6">
                            <div><b-form-textarea id="textarea" v-model="form.output" placeholder="Output..." rows="10" max-rows="10"></b-form-textarea></div>
                            <br />
                            <div>
                                <b-form-select v-model="form.outputSelection" :options="options"></b-form-select>
                            </div>
                        </b-col>
                    </b-row>
                    <br />
                    <b-row>
                        <b-col sm="6"><b-button block variant="primary" type="submit">Convert</b-button></b-col>
                        <b-col sm="6"><b-button block variant="success">Copy</b-button></b-col>
                    </b-row>
                </b-form>
            </b-container>
        </section>
    </div>
</template>
<script lang="ts">
import Vue from 'vue'
import { required } from 'vuelidate/lib/validators'
const HeaderComponent = () => import('@/components/common/header.vue')
const FooterComponent = () => import('@/components/common/footer.vue')

export default Vue.extend({
    name: 'Index',
    components: {
        'header-component': HeaderComponent,
        'footer-component': FooterComponent,
    },
    computed: {},
    data() {
        return {
            form: {
                input: '',
                output: '',
                inputSelection: null,
                outputSelection: null,
            },
            validations: {
                form: {
                    input: {
                        required,
                    },
                },
            },
            options: [
                { value: null, text: 'Please select an option' },
                { value: 'camel-case', text: 'Camel Case (camelCase)' },
                { value: 'pascal-case', text: 'Pascal Case (PascalCase)' },
                { value: 'kebab-case', text: 'Kebab Case (kebab-case)' },
                { value: 'snake-case', text: 'Snake Case (snake_case)' },
                { value: 'dto', text: 'Data Transfer Object (POCOs,POJOs)' },
            ],
        }
    },
    methods: {
        onSubmit() {
            if (this.validateJSON(this.form.input)) {
                const result = JSON.stringify(this.toCamelCase(this.form.input.trim()), null, 2)
                this.form.output = result
            }
        },
        toTitleCase(value: string): string {
            return value.replace(/\w\S*/g, (txt) => {
                return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase()
            })
        },
        toCamelCase(value: string): string {
            return value
                .replace(/(?:^\w|[A-Z]|\b\w)/g, (word, index) => {
                    return index === 0 ? word.toLowerCase() : word.toUpperCase()
                })
                .replace(/\s+/g, '')
        },
        toPascalCase(value: string): string {
            return value
                .replace(/(?:^\w|[A-Z]|\b\w)/g, (word) => {
                    return word.toUpperCase()
                })
                .replace(/\s+/g, '')
        },
        toKebabCase(value: string): string {
            return value
                .replace(/([a-z])([A-Z])([0-9])/g, '$1-$2')
                .replace(/\s+/g, '-')
                .toLowerCase()
                .trim()
        },

        toSnakeCase(value: string): string {
            return value
                .replace(/([a-z])([A-Z])([0-9])/g, '$1-$2')
                .replace(/\s+/g, '_')
                .toLowerCase()
                .trim()
        },
        validateJSON(value: string | null): boolean {
            try {
                if (!value) {
                    return false
                }
                JSON.parse(value)
                return true
            } catch (exception) {
                return false
            }
        },
    },
})
</script>

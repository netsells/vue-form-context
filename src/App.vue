<template>
    <div id="app">
        <pre>{{ formData }}</pre>

        <form-context
            v-model="formData"
            :states="{
                errors: {
                    foo: 'Error',
                },
            }"
        >

            <form-value path="foo">
                <template v-slot="{ value, states: { errors } }">
                    <input v-model="value.model" />
                    <p v-if="errors.foo">
                        {{ errors.foo }}
                    </p>
                </template>
            </form-value>

            <form-value path="some.path[0]">
                <template v-slot="{ value }">
                    <input v-model="value.model" />
                </template>
            </form-value>

        </form-context>
    </div>
</template>

<script>
    import FormContext from './components/FormContext';
    import FormValue from './components/FormValue';

    export default {
        name: 'app',

        components: {
            FormContext,
            FormValue,
        },

        data() {
            return {
                formData: {},
            };
        },
    };
</script>

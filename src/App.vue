<template>
    <div id="app">
        <pre>{{ formData }}</pre>

        <form-context v-model="formData">

            <form-value path="foo">
                <template v-slot="{ value }">
                    <input v-model="value.computed" />
                </template>
            </form-value>

            <form-value path="bar">
                <template v-slot="{ value }">
                    <input v-model="value.computed" />
                </template>
            </form-value>

            <form-value path="some.path">
                <template v-slot="{ value }">
                    <input v-model="value.computed" />
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

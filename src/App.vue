<template>
    <div id="app">
        <form-context>
            <form-value path="foo">
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
    };
</script>

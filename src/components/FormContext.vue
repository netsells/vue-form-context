<template>
    <div>
        <pre>{{ formData }}</pre>
        <slot />
    </div>
</template>

<script>
    import set from 'lodash.set';

    export default {
        name: 'form-context',

        props: {
            defaultValue: {
                type: Object,
                default() {
                    return {};
                },
            },
        },

        data() {
            return {
                formData: this.defaultValue,
            };
        },

        provide() {
            return {
                formData: this.formData,
                setFormData: this.setFormData,
            };
        },

        methods: {
            setFormData(path, value) {
                const formData = { ...this.formData };

                set(formData, path, value);

                this.formData = formData;
            },
        },
    };
</script>

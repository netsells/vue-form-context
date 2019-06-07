<template>
    <div>
        <slot />
    </div>
</template>

<script>
    import set from 'lodash.set';

    export default {
        name: 'form-context',

        props: {
            value: {
                type: Object,
                required: true,
            },
        },

        provide() {
            return {
                formData: this.value,
                setFormData: this.setFormData,
            };
        },

        methods: {
            setFormData(path, value) {
                const formData = { ...this.value };

                set(formData, path, value);

                this.$emit('input', formData);
            },
        },
    };
</script>

<template>
    <div>
        <slot :value="value" />
    </div>
</template>

<script>
    import get from 'lodash.get';

    export default {
        name: 'form-value',

        props: {
            path: {
                type: String,
                required: true,
            },
        },

        inject: [
            'formData',
            'setFormData',
        ],

        computed: {
            value() {
                const self = this;

                return {
                    get computed() {
                        return get(self.formData, self.path);
                    },

                    set computed(value) {
                        self.setFormData(self.path, value);
                    },
                };
            },
        },
    };
</script>

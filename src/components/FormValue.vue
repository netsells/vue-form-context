<template>
    <div>
        <slot :value="value" :states="states" />
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
            'states',
            'setFormData',
        ],

        computed: {
            value() {
                const self = this;

                return {
                    get model() {
                        return get(self.formData, self.path);
                    },

                    set model(value) {
                        self.setFormData(self.path, value);
                    },
                };
            },
        },
    };
</script>

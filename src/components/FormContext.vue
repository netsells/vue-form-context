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

            states: {
                type: Object,
                default() {
                    return {};
                },
            },
        },

        data() {
            return {
                stateStore: this.states,
            };
        },

        provide() {
            return {
                formData: this.value,
                states: this.stateStore,
                setFormData: this.setFormData,
                setStates: this.setStates,
            };
        },

        watch: {
            states: {
                immediate: true,
                deep: true,
                handler(states) {
                    this.stateStore = { ...states };
                },
            },
        },

        methods: {
            setFormData(path, value) {
                const formData = { ...this.value };

                set(formData, path, value);

                this.$emit('input', formData);
            },

            setStates(path, value) {
                set(this.stateStore, path, value);

                this.$emit('update:states', this.stateStore);
            },
        },
    };
</script>

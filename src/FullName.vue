<template>
    <div>
        <div class="col-xs-12 col-sm-8 col-md-6">
            <input type="text"
                id="firstName"
                class="form-control"
                @input="nameChanged(true, $event)"
                :value="firstName">
        </div>
        <div class="col-xs-12 col-sm-8 col-md-6">
            <input type="text"
                    id="lastName"
                    class="form-control"
                    @input="nameChanged(false, $event)"
                    :value="lastName">
        </div>

    </div>
</template>

<script>
    export default {
        props: ['value'],
        methods: {
            nameChanged (isFirst, event) {
                let name = '';
                if (isFirst) {
                    name = event.target.value + ' ' + this.lastName;
                } else {
                    name = this.firstName + ' ' + event.target.value;
                }
                this.value = name;
                this.$emit('input', this.value);
            }
        },
        computed: {
            firstName () {
                return this.value.split(' ')[0];
            },
            lastName () {
                return this.value.split(' ')[1];
            }
        }
    }
</script>

<style scoped>

</style>


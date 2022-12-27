<template>
    <div>
        <input
            :id="subField.name"
            :name="subField.name"
            type="file"
            class="w-full form-control form-input form-input-bordered"
            v-bind="subField.attributes"
        />
    </div>

</template>

<script>

    export default {

        props: [
            'subField',
            'value'
        ],

    }
</script>
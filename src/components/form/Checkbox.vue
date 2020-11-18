<template>
    <div class="form-checkbox">
        <input
            type="checkbox"
            :checked="checked"
            :id="id"
            @change="onChange"
            :name="name" />
        <label
            :for="id"
            :class="`form-checkbox--label ${checked && 'form-checkbox--label form-checkbox--checked'}`">
            {{ label }}
        </label>
    </div>

</template>

<script>
export default {
    name: 'CheckboxComponent',
    props: [
        'label',
        'checked',
        'name',
        'id',
        'onChange',
    ],
}
</script>

<style scoped>
.form-checkbox {
    display: flex;
    flex-flow: row nowrap;
    align-items: center;
}

.form-checkbox .form-checkbox--checked {
    text-decoration: line-through;
}

.form-checkbox .form-checkbox--label {
    margin-left: 8px;
}
</style>
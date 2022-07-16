<template>
  <div class="user-form">
    <div class="flex">
        <div class="form-fields">
            <h2>Информация о себе:</h2>
            <div 
            class="form-group"
            v-for="(fieldValue, fieldLabel, index) in formFields"
            :key="index"
            >
                <label :for="fieldLabel">{{fieldLabel}}</label>
                <input 
                type="text" 
                class="form-control"
                :id="fieldLabel"
                v-model="formFields[fieldLabel]"
                />
            </div>
            <button class="btn btn-primary mt-3" type="submit">Сохранить</button>
        </div>
        <div class="user-info">
            <h2>Предпросмотр:</h2>
            <p v-for="(fieldValue, fieldLabel, index) in formFields" :key="index">
            {{`${fieldLabel}: ${fieldValue}`}}
            </p>
        </div>
    </div>
    <div class="form-group">
        <label for="additionalField">Дополнительное поле:</label>
        <input 
        type="text" 
        class="form-control" 
        id="additionalField"
        v-model="additionalField"
        />
    </div>
    <button 
    class="btn btn-success mt-3"
    @click="addNewField"
    >
    Добавить</button>
  </div>
</template>


<script>
export default {
    name: 'UserForm',
    data() {
        return {
            formFields: {
                firstName: '',
                secondName: '',
                lastName: '',
            },
            additionalField: '',
        }
    },
    methods: {
        addNewField() {
            this.formFields[this.additionalField] = '';
        }
    }
}
</script>

<style lang="scss" scoped>
input {
  width: 400px;
}
.form-fields {
  margin-right: 50px;
  margin-bottom: 50px;
}
</style>
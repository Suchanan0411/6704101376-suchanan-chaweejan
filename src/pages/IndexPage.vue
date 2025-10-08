<template>
  <q-page>
    <q-form
      ref="form"
      @submit.prevent="submitForm"
      @reset="resetForm"
      :autofocus="true"
      :autocorrect="false"
      :autocomplete="false"
      :spellcheck="false"
    >
      <q-input
        filled
        v-model="formData.name"
        label="ชื่อ"
        :rules="[val => val && val.length > 0 || 'กรุณากรอกชื่อ']"
      />
      <q-input
        filled
        v-model="formData.email"
        label="อีเมล"
        type="email"
        :rules="[val => val && val.length > 0 || 'กรุณากรอกอีเมล']"
      />
      <q-btn label="ส่งข้อมูล" type="submit" color="primary" />
      <q-btn label="รีเซ็ต" type="reset" color="secondary" flat />
    </q-form>
  </q-page>
</template>

<script setup>
import { ref } from 'vue';

const formData = ref({
  name: '',
  email: ''
});

const form = ref(null);

function submitForm() {
  if (form.value.validate()) {
    console.log('ข้อมูลที่กรอก:', formData.value);
    // ที่นี่คุณสามารถส่งข้อมูลไปยัง API หรือทำการประมวลผลอื่น ๆ ได้
  }
}

function resetForm() {
  formData.value = {
    name: '',
    email: ''
  };
}
</script>

---
description: Form handling and validation for admin panel
globs: ["**/components/**/*Form*.vue", "**/composables/use*Form*.ts"]
---

# Forms & Validation Rules

## Form Structure  

**Use Element Plus form components**

```vue
<script setup lang="ts">
import { reactive, ref } from 'vue'
import type { FormInstance, FormRules } from 'element-plus'

interface OrderForm {
  customerName: string
  items: string[]
  notes: string
}

const formRef = ref<FormInstance>()
const form = reactive<OrderForm>({
  customerName: '',
  items: [],
  notes: ''
})

const rules: FormRules = {
  customerName: [
    { required: true, message: 'Name is required', trigger: 'blur' }
  ]
}

const handleSubmit = async () => {
  if (!formRef.value) return
  
  await formRef.value.validate()
  // Submit logic
}
</script>

<template>
  <el-form ref="formRef" :model="form" :rules="rules">
    <el-form-item label="Customer Name" prop="customerName">
      <el-input v-model="form.customerName" />
    </el-form-item>
    <el-form-item>
      <el-button type="primary" @click="handleSubmit">Submit</el-button>
    </el-form-item>
  </el-form>
</template>
```

## Validation  

- Use Element Plus built-in validation
- Define rules object typed as `FormRules`
- Validate on submit via `formRef.validate()`
- Show errors inline via form-item

## Form Submission  

**Prevent duplicate submissions**

```typescript
const submitting = ref(false)

const handleSubmit = async () => {
  if (submitting.value) return
  
  submitting.value = true
  try {
    await formRef.value?.validate()
    await orderService.createOrder(form)
    // Success feedback
  } catch (error) {
    // Error handling
  } finally {
    submitting.value = false
  }
}
```

## Error Handling  

- Field errors: Shown by Element Plus automatically
- Form-level errors: Show via `ElMessage.error()`
- API errors: Propagate from service, display in UI

## Form Reset  

```typescript
const resetForm = () => {
  formRef.value?.resetFields()
}
```

## Custom Input Components  

If creating custom inputs:

```typescript
interface Props {
  modelValue: string
}

interface Emits {
  (e: 'update:modelValue', value: string): void
}

const props = defineProps<Props>()
const emit = defineEmits<Emits>()
```

Use with `v-model` in parent component

<script setup lang="ts">
import { ref } from 'vue'
import { useForm } from 'vee-validate'
import { toTypedSchema } from '@vee-validate/zod'
import * as z from 'zod'
import { UiButton } from '@/components/ui/button'
import { UiInput } from '@/components/ui/input'
import {
  FormControl,
  FormDescription,
  FormField,
  FormItem,
  FormLabel,
  FormMessage,
} from '@/components/ui/form'

const isFormValid = ref(false)

const formSchema = toTypedSchema(
  z.object({
    firstname: z
      .string({ required_error: 'First name is required' })
      .min(3, { message: 'Min of 3 characters required' }),
    surname: z
      .string({ required_error: 'Surname is required' })
      .min(3, { message: 'Min of 3 characters required' }),
    mobile: z.string().regex(/^\+[1-9]\d{1,14}$/, 'Invalid mobile number'),
  }),
)

const form = useForm({
  validationSchema: formSchema,
})

const onSubmit = form.handleSubmit((values) => {
  // All passed validation
  isFormValid.value = true
})
</script>

<template>
  <div>
    <h1 class="pb-4">The form</h1>
    <p v-if="isFormValid">You have submitted the form.</p>
    <form @submit="onSubmit" class="max-w-xs space-y-4 py-8">
      <FormField v-slot="{ componentField }" name="firstname">
        <FormItem>
          <FormLabel>First name</FormLabel>
          <FormControl>
            <UiInput type="text" placeholder="Enter firstname" v-bind="componentField" />
          </FormControl>
          <FormMessage />
        </FormItem>
      </FormField>
      <FormField v-slot="{ componentField }" name="middlename">
        <FormItem>
          <FormLabel>Middle name</FormLabel>
          <FormControl>
            <UiInput type="text" placeholder="Enter middle name" v-bind="componentField" />
          </FormControl>
          <FormMessage />
        </FormItem>
      </FormField>
      <FormField v-slot="{ componentField }" name="surname">
        <FormItem>
          <FormLabel>Surname</FormLabel>
          <FormControl>
            <UiInput type="text" placeholder="Enter surnname" v-bind="componentField" />
          </FormControl>
          <FormMessage />
        </FormItem>
      </FormField>
      <FormField v-slot="{ componentField }" name="mobile">
        <FormItem>
          <FormLabel>Mobile</FormLabel>
          <FormControl>
            <UiInput type="text" placeholder="Enter mobile" v-bind="componentField" />
          </FormControl>
          <FormMessage />
        </FormItem>
      </FormField>
      <UiButton type="submit"> Submit </UiButton>
    </form>
  </div>
</template>

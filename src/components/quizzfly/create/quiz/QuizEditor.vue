<script setup lang="ts">
import { Input } from '@/components/ui/input'
import EditableText from '@/components/base/EditableText.vue'
import AnswerSetting from '@/components/quizzfly/create/quiz/AnswerSetting.vue'

const title = ref('')

const handleFocusInputTitle = () => {
  nextTick(() => {
    titleInputRef.value?.$el?.focus()
  })
}

const titleInputRef = ref<InstanceType<typeof Input>>()
</script>
<template>
  <div class="w-full h-full flex flex-col gap-5 p-5 overflow-hidden">
    <!-- question -->
    <div class="">
      <EditableText
        :value="title"
        :click-callback="handleFocusInputTitle"
      >
        <template #input="{ finishEditing }">
          <Input
            ref="titleInputRef"
            v-model="title"
            placeholder="Enter your question"
            class="text-2xl font-medium h-12"
            @blur="finishEditing"
          />
        </template>
        <template #default="{}">
          <p
            class="py-1 px-2 rounded-lg border-2 border-transparent hover:border-primary text-2xl font-medium"
          >
            {{ title || 'Enter question' }}
          </p>
        </template>
      </EditableText>
    </div>

    <!-- picture -->
    <div class="flex justify-center flex-auto">
      <div class="w-[80%] h-full bg-slate-100 rounded-lg"></div>
    </div>
    <!-- answer -->
    <AnswerSetting />
  </div>
</template>

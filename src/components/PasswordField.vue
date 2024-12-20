<template>
  <div class="password-field-container">
    <label :for="id">{{ labelText }}</label>
    <div>
      <input
        type="password"
        :id="id"
        :value="modelValue"
        @input="updateModelValue"
      />
      <!-- TODO add a toogle visibility button here -->
    </div>
  </div>
</template>

<script setup>
defineProps({
  modelValue: {
    type: String,
    required: true,
  },
  id: {
    type: String,
    required: true,
    default: "text",
  },
  labelText: {
    type: String,
    required: true,
    default: "text",
  },
});

const emit = defineEmits(["update:modelValue"]);

function updateModelValue(event) {
  emit("update:modelValue", event.target.value);
}
</script>

<style scoped>
.password-field-container {
  display: flex;
  flex-direction: column;
}

.password-field-container label {
  font-size: 14px;
}

.password-field-container input {
  height: 32px;
  border: none;
  border-bottom: 1px solid #474747;
  flex: 1;
}

.password-field-container div {
  display: flex;
  align-items: center;
}
</style>

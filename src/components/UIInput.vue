<template>
  <div
    class="form-input"
    :style="{ width: width }"
  >
    <input
      :value="value"
      :type="type"
      :id="name"
      :name="name"
      :placeholder="placeholder"
      class="input__text"
      @input="updateValue"
    >
    <label :for="name" class="input__label">{{ label }}</label>
    <TransitionGroup>
      <div
        v-for="error of errors"
        :key="error.$uid"
        class="form-error">
        <p>{{ error.$message }}</p>
      </div>
    </TransitionGroup>
  </div>
</template>

<script setup>
defineProps({
  value: {
    type: String,
    default: ''
  },
  name: {
    type: String,
    required: true
  },
  type: {
    type: String,
    default: 'text'
  },
  placeholder: {
    type: String,
    required: true
  },
  label: {
    type: String,
    required: true
  },
  width: {
    type: String,
    default: '300px'
  },
  errors: {
    type: Array,
    required: false
  },
});

const emit = defineEmits(['update:value']);

const updateValue = (event) => {
  emit('update:value', event.target.value);
}
</script>

<style lang="scss">
.form {
  &-input {
    margin-bottom: 30px;
    position: relative;
  }
  &-error {
    background: var(--color-danger);
    margin-top: 4px;
    border-radius: 7px;
    font-size: 13px;
    color: var(--color-white);
    padding: 5px;
  }
}

.input {
  &__text {
    border: 1px solid var(--color-primary);
    padding: 0 10px;
    height: 40px;
    border-radius: 7px;
    font-size: 15px;
    width: 100%;
    position: relative;
    z-index: 1;

    &:focus {
      & + .input__label {
        z-index: 1;
        opacity: 1;
        top: -20px;
      }
    }

    &:not(:placeholder-shown) {
      & + .input-label {
        z-index: 1;
        opacity: 1;
        top: -20px;
      }
    }
  }
  &__label {
    font-weight: bold;
    display: block;
    position: absolute;
    top: 20px;
    opacity: 0;
    z-index: -1;
    transition: .3s;
    font-size: 13px;
    color: var(--color-primary);
  }
}

.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>

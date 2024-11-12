<script setup lang="ts">
import { ref } from 'vue';
import {
  TagsInputInput,
  TagsInputItem,
  TagsInputItemDelete,
  TagsInputItemText,
  TagsInputRoot,
  ComboboxInput,
  ComboboxRoot,
  ComboboxViewport,
  ComboboxAnchor,
  ComboboxContent,
  ComboboxTrigger,
  ComboboxEmpty,
  ComboboxGroup,
  ComboboxItemIndicator,
  ComboboxLabel,
  ComboboxItem,
} from 'radix-vue';
import { Icon } from '@iconify/vue';

const options = ['Apple', 'Banana', 'Blueberry', 'Grapes', 'Pineapple'];
const vegetables = ['Aubergine', 'Broccoli', 'Carrot', 'Courgette', 'Leek'];

const modelValue = ref(['Apple', 'Banana']);
const newValue = ref('');

const onSelected = (v) => {
  console.log('v', v);
};
</script>

<template>
  <TagsInputRoot
    v-model="modelValue"
    class="flex gap-2 items-center border p-2 rounded-lg w-full max-w-[480px] flex-wrap border-blackA7 bg-white"
  >
    <TagsInputItem
      v-for="item in modelValue"
      :key="item"
      :value="item"
      class="text-white flex shadow-md items-center justify-center gap-2 bg-green8 aria-[current=true]:bg-green9 rounded p-1"
    >
      <TagsInputItemText class="text-sm pl-1" />
      <TagsInputItemDelete
        class="p-0.5 rounded bg-transparent hover:bg-blackA4"
      >
        <Icon icon="lucide:x" />
      </TagsInputItemDelete>
    </TagsInputItem>

    <!-- <TagsInputInput
      placeholder="Fruits..."
      class="text-sm focus:outline-none flex-1 rounded text-green9 bg-transparent placeholder:text-mauve9 px-1"
    /> -->
    <ComboboxRoot v-model="newValue" @selected="onSelected">
      <ComboboxAnchor
        class="min-w-[60px] inline-flex items-center justify-between rounded px-[15px] text-[13px] p-1 leading-none h-fit gap-[5px] bg-white text-grass11 shadow-[0_2px_10px] shadow-black/10 hover:bg-mauve3 focus:shadow-[0_0_0_2px] focus:shadow-black data-[placeholder]:text-grass9 outline-none"
      >
        <ComboboxInput
          placeholder="--"
          class="text-sm h-fit focus:outline-none flex-1 rounded text-green9 bg-transparent placeholder:text-mauve9 px-1"
        />
        <!-- <ComboboxInput
          class="!bg-transparent outline-none text-grass11 h-full selection:bg-grass5 placeholder-mauve8"
          placeholder="Placeholder..."
        /> -->
        <ComboboxTrigger>
          <Icon icon="radix-icons:chevron-down" class="h-4 w-4 text-grass11" />
        </ComboboxTrigger>
      </ComboboxAnchor>

      <ComboboxContent
        class="absolute z-10 mt-2 min-w-12 bg-white overflow-hidden rounded shadow-[0px_10px_38px_-10px_rgba(22,_23,_24,_0.35),_0px_10px_20px_-15px_rgba(22,_23,_24,_0.2)] will-change-[opacity,transform] data-[side=top]:animate-slideDownAndFade data-[side=right]:animate-slideLeftAndFade data-[side=bottom]:animate-slideUpAndFade data-[side=left]:animate-slideRightAndFade"
      >
        <ComboboxViewport class="p-[5px]">
          <ComboboxEmpty
            class="text-mauve8 text-xs font-medium text-center p-2"
          >No options</ComboboxEmpty>

          <ComboboxGroup>
            <ComboboxLabel
              class="px-[25px] text-xs leading-[25px] text-mauve11"
            >
              Fruits
            </ComboboxLabel>

            <ComboboxItem
              v-for="(option, index) in options"
              :key="index"
              class="text-[13px] leading-none text-grass11 rounded-[3px] flex items-center h-[25px] pr-[35px] pl-[25px] relative select-none data-[disabled]:text-mauve8 data-[disabled]:pointer-events-none data-[highlighted]:outline-none data-[highlighted]:bg-grass9 data-[highlighted]:text-grass1"
              :value="option"
            >
              <ComboboxItemIndicator
                class="absolute left-0 w-[25px] inline-flex items-center justify-center"
              >
                <Icon icon="radix-icons:check" />
              </ComboboxItemIndicator>
              <span>
                {{ option }}
              </span>
            </ComboboxItem>
            <ComboboxSeparator class="h-[1px] bg-grass6 m-[5px]" />
          </ComboboxGroup>

          <ComboboxGroup>
            <ComboboxLabel
              class="px-[25px] text-xs leading-[25px] text-mauve11"
            >
              Vegetables
            </ComboboxLabel>
            <ComboboxItem
              v-for="(option, index) in vegetables"
              :key="index"
              class="text-[13px] leading-none text-grass11 rounded-[3px] flex items-center h-[25px] pr-[35px] pl-[25px] relative select-none data-[disabled]:text-mauve8 data-[disabled]:pointer-events-none data-[highlighted]:outline-none data-[highlighted]:bg-grass9 data-[highlighted]:text-grass1"
              :value="option"
            >
              <ComboboxItemIndicator
                class="absolute left-0 w-[25px] inline-flex items-center justify-center"
              >
                <Icon icon="radix-icons:check" />
              </ComboboxItemIndicator>
              <span>
                {{ option }}
              </span>
            </ComboboxItem>
          </ComboboxGroup>
        </ComboboxViewport>
      </ComboboxContent>
    </ComboboxRoot>
  </TagsInputRoot>
</template>

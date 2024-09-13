<template>
  <div class="text-center">
    <div @click="dialog = true" class="truncate max-w-40">{{ item.app }}</div>

    <v-dialog v-model="dialog" width="auto">
      <v-card width="500" prepend-icon="mdi-cast-audio-variant" title="App" color="#3174c3"
        ><div class="px-10 py-6 bg-white" >
          {{ item.app }}
        </div>
        <!-- <template v-slot:actions>
          <v-btn class="ms-auto" text="Ok" @click="dialog = false"></v-btn>
        </template> -->
      </v-card>
    </v-dialog>
  </div>
</template>

<script setup>
const props = defineProps(["item", "status"]);

const dialog = ref(props.status);
const item = props.item;
</script>

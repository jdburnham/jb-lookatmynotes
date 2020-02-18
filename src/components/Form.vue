<template>
  <div class="bg-white w-1/2 m-4 rounded-lg shadow p-4 mx-auto text-black">
    <label class="block">
      <span class="text-gray-700">Title</span>
      <input
        v-model="title"
        class="form-input mt-1 block w-full"
        placeholder="My New Note"
      />
    </label>
    <label class="block mt-4">
      <span class="text-gray-700">Content</span>
      <textarea
        v-model="content"
        class="form-textarea mt-1 block w-full"
        rows="3"
        placeholder="The content of my new super cool note."
      ></textarea>
    </label>
    <div class="buttons w-full flex justify-center">
      <button
        class="bg-gray-500 hover:bg-gray-700 text-white font-bold py-2 px-4 rounded mt-4 mr-4 flex-grow"
        @click="$router.push('/')"
      >
        Cancel
      </button>
      <button
        v-if="!edit"
        class="bg-blue-700 hover:bg-blue-900 text-white font-bold py-2 px-4 rounded mt-4 flex-grow"
        @click="add"
      >
        Add
      </button>
      <button
        v-else
        class="bg-green-700 hover:bg-green-900 text-white font-bold py-2 px-4 rounded mt-4 flex-grow"
        @click="save"
      >
        Edit
      </button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Form',
  data() {
    return {
      title: '',
      content: ''
    }
  },
  methods: {
    add() {
      this.$store.dispatch('addNote', {
        id: '?',
        title: this.title,
        content: this.content
      })
      this.$router.push('/')
    }
  }
}
</script>

<style lang="scss" scoped></style>

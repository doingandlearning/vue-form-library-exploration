<script setup lang="ts">
import { ref } from "vue";

const form = ref({
  name: '',
  email: '',
  password: '',
  favouriteConsole: '',
  socialMedia: '',
  interests: []
});

const errors = ref<Record<string, null | string>>({
  name: null,
  email: null,
  password: null,
  favouriteConsole: null,
  socialMedia: null,
  interests: null
})

function handleSubmit() {
  if (form.value.name === "") {
    errors.value.name = "You need to provide a name."
  } else {
    errors.value.name = null;
  }

  if (form.value.password.length < 6) {
    errors.value.password = "Your password should be at least 6 characters."
  } else {
    errors.value.password = null
  }
  if (form.value.socialMedia === "") {
    errors.value.socialMedia = "You should select your favourite platform."
  } else {
    errors.value.socialMedia = null
  }
  if (form.value.interests.length === 0) {
    errors.value.interests = "You should select at least one interest."
  } else {
    errors.value.interests = null
  }
  console.log(form.value)
}
</script>

<template>
  <div class="p-6 max-w-sm mx-auto bg-white rounded-xl shadow-md flex items-center space-x-4">
    <form @submit.prevent="handleSubmit">
      <div class="mb-6">
        <label for="name" class="block text-gray-700 text-sm font-bold mb-2">Name</label>
        <input type="text" id="name" v-model="form.name"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
        <p v-if="errors.name" class="text-red-500 text-xs italic">{{ errors.name }}</p>
      </div>
      <div class="mb-6">
        <label for="email" class="block text-gray-700 text-sm font-bold mb-2">Email</label>
        <input type="email" id="email" v-model="form.email"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
        <p v-if="errors.email" class="text-red-500 text-xs italic">{{ errors.email }}</p>
      </div>
      <div class="mb-6">
        <label for="password" class="block text-gray-700 text-sm font-bold mb-2">Password</label>
        <input type="password" id="password" v-model="form.password"
          class="shadow appearance-none border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline" />
        <p v-if="errors.password" class="text-red-500 text-xs italic">{{ errors.password }}</p>
      </div>

      <div class="mb-6">
        <label for="favouriteConsole" class="block text-gray-700 text-sm font-bold mb-2">Favourite Console</label>
        <p v-if="errors.favouriteConsole" class="text-red-500 text-xs italic">{{ errors.favouriteConsole }}</p>
        <div>
          <label class="inline-flex items-center">
            <input type="radio" class="form-radio h-4 w-4 text-indigo-600" name="favouriteConsole" value="ps"
              v-model="form.favouriteConsole">
            <span class="ml-2">PlayStation</span>
          </label>
          <label class="inline-flex items-center ml-6">
            <input type="radio" class="form-radio h-4 w-4 text-indigo-600" name="favouriteConsole" value="xbox"
              v-model="form.favouriteConsole">
            <span class="ml-2">XBox</span>
          </label>
          <label class="inline-flex items-center ml-6">
            <input type="radio" class="form-radio h-4 w-4 text-indigo-600" name="favouriteConsole" value="steam"
              v-model="form.favouriteConsole">
            <span class="ml-2">Steam Deck</span>
          </label>
        </div>
      </div>

      <div class="mb-6">
        <label for="socialMedia" class="block text-gray-700 text-sm font-bold mb-2">Favourite Social Channel</label>
        <p v-if="errors.socialMedia" class="text-red-500 text-xs italic">{{ errors.socialMedia }}</p>
        <select id="socialMedia" v-model="form.socialMedia"
          class="shadow appearance-noe border rounded w-full py-2 px-3 text-gray-700 leading-tight focus:outline-none focus:shadow-outline">
          <option value="">Select a platform</option>
          <option value="facebook">Facebook</option>
          <option value="twitter">Twitter</option>
          <option value="instagram">Instagram</option>
          <option value="tiktok">TikTok</option>
          <option value="mastadon">Mastadon</option>

        </select>
      </div>

      <div class="mb-6">
        <label for="interests" class="block text-gray-700 text-sm font-bold mb-2">Interests</label>
        <p v-if="errors.interests" class="text-red-500 text-xs italic">{{ errors.interests }}</p>
        <label class="inline-flex items-center ml-6">
          <input type="checkbox" class="form-checkbox h-4 w-4 text-indigo-600" name="favouriteConsole" value="sport"
            v-model="form.interests">
          <span class="ml-2">Sport</span>
        </label>
        <label class="inline-flex items-center ml-6">
          <input type="checkbox" class="form-checkbox h-4 w-4 text-indigo-600" name="favouriteConsole" value="ttrpg"
            v-model="form.interests">
          <span class="ml-2">TTRPG</span>
        </label>
        <label class="inline-flex items-center ml-6">
          <input type="checkbox" class="form-checkbox h-4 w-4 text-indigo-600" name="favouriteConsole" value="music"
            v-model="form.interests">
          <span class="ml-2">Music</span>
        </label>
        <label class="inline-flex items-center ml-6">
          <input type="checkbox" class="form-checkbox h-4 w-4 text-indigo-600" name="favouriteConsole" value="movies"
            v-model="form.interests">
          <span class="ml-2">Movies</span>
        </label>
      </div>

      <div class="flex justify-center">
        <button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold pb-2 px-4 rounded focus:outline-none focus:shadow-outline"
          type="submit">
          Submit
        </button>
      </div>
    </form>
  </div>
</template>

<template>
 
  <div class="flex justify-center items-center min-h-screen bg-gray-100">
 
    <div v-if="loading" class="text-center text-muted">
      <Spinner class="w-8"/>
    </div>
      <div v-else class="magazine-container flex flex-col md:flex-row bg-white shadow-lg rounded p-6">
   
      <div class="magazine-detail flex-1 md:mr-6">
        <h1 class=" name-magazine font-semibold mb-2">{{ magazine.name || "Untitled" }}</h1>
        <p><strong>Author:</strong> {{ magazine.author || "Unknown" }}</p>
        <p><strong>ISSN:</strong> {{ magazine.issn || "N/A" }}</p>
        <p><strong>Category:</strong> {{ magazine.category || "Uncategorized" }}</p>
        <p><strong>Publisher:</strong> {{ magazine.publisher || "Unknown" }}</p>
        <div class="mt-2">
          <strong>Purchase:</strong>
          <Badge
            :variant="'solid'"
            :theme="gray"
            size="md"
            v-if="magazine && magazine.purchase"
          >
            {{ magazine.purchase }}
          </Badge>
        </div>
        <div class="mt-4">
          <span class="font-bold">Description</span>
          <div v-html="magazine.description || 'Description not available'" class="description-magazine"></div>
        </div>
        <div class="mt-4">
          <Rating size="lg" label="Rate Magazine" />
        </div>
        <div class="p-1">
  <Button
    :variant="'solid'"
    :ref_for="true"
    theme="blue"
    size="sm"
    label="Button"
    :loading="false"
    :loadingText="null"
    :disabled="false"
    :link="null"
    @click="navigateHome"
    class="px-8 py-5 mt-20 bg-blue-500 text-white rounded hover:bg-blue-600"
  >
    List
  </Button>
</div>
      </div>

      <div class="magazine-image flex-1 flex justify-center items-center">
        <img
          :src="magazine.image"
          alt="Magazine Cover"
          class="w-full md:w-auto h-auto max-w-sm rounded"
          v-if="magazine.image"
        />
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  props: ["name"],
  data() {
    return {
      magazine: null,
      loading: true,
    };
  },
  methods: {
    async fetchMagazineDetails() {
      const API_KEY = "31e370a5f806344";
      const API_SECRET = "8b0e2e7c3c71948";

      try {
        const response = await axios.get(
          `http://magazines.localhost:8002/api/resource/Magazine/${this.name}`,
          {
            headers: {
              Authorization: `token ${API_KEY}:${API_SECRET}`,
            },
          }
        );
        this.magazine = response.data.data;
      } catch (error) {
        console.error("Error fetching magazine details:", error);
      } finally {
        this.loading = false;
      }
    },
    navigateHome() {
      this.$router.push("/");
    },
  },
  mounted() {
    this.fetchMagazineDetails();
  },
};
</script>
<style>
.magazine-container {
  max-width: 800px;
  width: 100%;
}
.name-magazine{
  font-size: xx-large;
  color: rgb(0, 81, 255);
}
.description-magazine{
  text-align: justify;
  color: rgb(80, 79, 79);
}
</style>

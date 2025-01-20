<template>
  <div class="flex flex-col items-center bg-gray-100">
    <h1 class="magazine-heading">MAGAZINES LIST</h1>
    <div v-if="loading" class="text-center text-muted">
      <Spinner class="w-8" />
    </div>
    <div v-else class="w-full max-w-4xl">
      <div
        v-for="magazine in magazines"
        :key="magazine.name"
        class=" card flex flex-col md:flex-row items-center border rounded shadow-sm p-4 mb-4 bg-card bg-white"
        @click="navigateToDetail(magazine.name)"
      >
        <div class="flex-shrink-0 mb-4 md:mb-0 md:mr-6">
          <img
            :src="magazine.image"
            alt="Magazine Cover"
            v-if="magazine.image"
            class="w-32 h-auto object-cover rounded"
          />
        </div>

        <div class="flex-1">
          <h2 class="text-lg font-semibold">{{ magazine.name || "Untitled" }}</h2>
          <p v-if="magazine && magazine.author" class="text-muted">
            <strong>Author:</strong> {{ magazine.author || "Unknown" }}
          </p>
          <p v-if="magazine && magazine.issn" class="text-muted">
            <strong>ISSN:</strong> {{ magazine.issn }}
          </p>
          <p v-if="magazine && magazine.category" class="text-muted">
            <strong>Category:</strong> {{ magazine.category }}
          </p>
          <p v-if="magazine && magazine.publisher" class="text-muted">
            <strong>Publisher:</strong> {{ magazine.publisher }}
          </p>
          <div class="mt-2">
            <strong>Purchase:</strong>
            <Badge
              :variant="'solid'"
              :theme="gray"
              size="sm"
              v-if="magazine && magazine.purchase"
            >
              {{ magazine.purchase }}
            </Badge>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  data() {
    return {
      magazines: [],
      loading: true,
    };
  },
  methods: {
    async fetchMagazines() {
      const API_KEY = "31e370a5f806344";
      const API_SECRET = "8b0e2e7c3c71948";

      try {
        const response = await axios.get(
          "http://magazines.localhost:8002/api/resource/Magazine",
          {
            params: {
              fields: JSON.stringify([
                "name",
                "author",
                "image",
                "purchase",
                "issn",
                "category",
                "publisher",
                "description"
              ]),
            },
            headers: {
              Authorization: `token ${API_KEY}:${API_SECRET}`,
            },
          }
        );
        console.log("API Response:", response.data.data);
        this.magazines = response.data.data;
      } catch (error) {
        console.error("Error fetching magazines:", error);
      } finally {
        this.loading = false;
      }
    },
    navigateToDetail(name) {
      this.$router.push({ name: "Magazine", params: { name } });
    },
  },
  mounted() {
    this.fetchMagazines();
  },
};
</script>

<style>
img {
  width: 200px;
}
.magazine-heading{
  font-size: xx-large;
  color: #808080;
}
.card{
  cursor: pointer;
}
</style>

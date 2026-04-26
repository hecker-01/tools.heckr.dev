<script setup>
import { getAllProjects } from "@/services/projectService";
import ToolCard from "@/components/ToolCard.vue";
import Footer from "@/components/Footer.vue";

const tools = getAllProjects();
</script>

<template>
  <div class="w-full min-h-screen overflow-x-hidden overflow-y-auto font-mono">
    <div class="max-w-5xl mx-auto px-4 sm:px-6 lg:px-8 py-8 md:py-16">
      <!-- Tool grid -->
      <div class="mb-10">
        <div class="text-catppuccin-subtle text-sm mb-4">~$ ls ~/tools</div>
        <div
          v-if="tools.length"
          class="grid sm:grid-cols-2 lg:grid-cols-3 gap-4"
        >
          <ToolCard v-for="tool in tools" :key="tool.slug" :tool="tool" />

          <!-- More coming -->
          <div
            class="flex flex-col rounded-md border border-catppuccin-surface/40 border-dashed bg-catppuccin-base/10 p-4 items-center justify-center text-center gap-2 min-h-[120px]"
          >
            <span class="text-catppuccin-text text-sm"
              >I'm always working on more...</span
            >
            <span class="text-catppuccin-subtle text-xs">Check back soon!</span>
          </div>
        </div>
        <p v-else class="text-catppuccin-subtle text-sm">
          no tools found — check back later.
        </p>
      </div>

      <Footer />
    </div>
  </div>
</template>

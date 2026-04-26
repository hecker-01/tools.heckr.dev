<script setup>
defineProps({
  tool: {
    type: Object,
    required: true,
  },
});
</script>

<template>
  <div
    class="flex flex-col rounded-md border border-catppuccin-surface/60 bg-catppuccin-base/20 overflow-hidden transition-all duration-200 card"
    :style="{ '--accent-color': tool.accentColorHex }"
  >
    <!-- Cover image -->
    <div
      v-if="tool.coverImage"
      class="w-full h-36 overflow-hidden flex-shrink-0"
    >
      <img
        :src="tool.coverImage"
        :alt="tool.title"
        class="w-full h-full object-cover transition-transform duration-300 hover:scale-105"
      />
    </div>

    <div class="flex flex-col flex-1 p-4">
      <!-- Title + status -->
      <div class="flex items-start justify-between gap-2 mb-1">
        <h2
          class="text-base font-bold leading-snug"
          :style="{ color: tool.accentColorHex }"
        >
          {{ tool.title }}
        </h2>
        <span
          class="flex-shrink-0 px-2 py-0.5 rounded text-xs capitalize mt-0.5"
          :class="{
            'bg-catppuccin-green/20 text-catppuccin-green': tool.status === 'active',
            'bg-catppuccin-yellow/20 text-catppuccin-yellow': tool.status === 'in-progress',
            'bg-catppuccin-red/20 text-catppuccin-red': tool.status === 'archived',
            'bg-catppuccin-blue/20 text-catppuccin-blue': tool.status === 'beta',
            'bg-catppuccin-peach/20 text-catppuccin-peach': tool.status === 'stale',
          }"
        >
          {{ tool.status }}
        </span>
      </div>

      <!-- Description -->
      <p class="text-sm text-catppuccin-text/80 mb-2 leading-relaxed flex-1">
        {{ tool.description }}
      </p>

<!-- Links -->
      <div class="flex flex-wrap gap-2 mt-auto">
        <a
          v-if="tool.url"
          :href="tool.url"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded border text-xs transition-colors hover:bg-catppuccin-surface/30"
          :style="{ borderColor: `${tool.accentColorHex}60`, color: tool.accentColorHex }"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor" class="w-3 h-3">
            <path d="M6.22 8.72a.75.75 0 0 0 1.06 1.06l5.22-5.22v1.69a.75.75 0 0 0 1.5 0v-3.5a.75.75 0 0 0-.75-.75h-3.5a.75.75 0 0 0 0 1.5h1.69L6.22 8.72Z" />
            <path d="M3.5 6.75c0-.69.56-1.25 1.25-1.25H7A.75.75 0 0 0 7 4H4.75A2.75 2.75 0 0 0 2 6.75v4.5A2.75 2.75 0 0 0 4.75 14h4.5A2.75 2.75 0 0 0 12 11.25V9a.75.75 0 0 0-1.5 0v2.25c0 .69-.56 1.25-1.25 1.25h-4.5c-.69 0-1.25-.56-1.25-1.25v-4.5Z" />
          </svg>
          Live Site
        </a>
        <a
          v-if="tool.download"
          :href="tool.download"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded border text-xs transition-colors hover:bg-catppuccin-surface/30"
          :style="{ borderColor: `${tool.accentColorHex}60`, color: tool.accentColorHex }"
        >
          <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 16 16" fill="currentColor" class="w-3 h-3">
            <path d="M8.75 2.75a.75.75 0 0 0-1.5 0v5.69L5.03 6.22a.75.75 0 0 0-1.06 1.06l3.5 3.5a.75.75 0 0 0 1.06 0l3.5-3.5a.75.75 0 0 0-1.06-1.06L8.75 8.44V2.75Z" />
            <path d="M3.5 9.75a.75.75 0 0 0-1.5 0v1.5A2.75 2.75 0 0 0 4.75 14h6.5A2.75 2.75 0 0 0 14 11.25v-1.5a.75.75 0 0 0-1.5 0v1.5c0 .69-.56 1.25-1.25 1.25h-6.5c-.69 0-1.25-.56-1.25-1.25v-1.5Z" />
          </svg>
          Download
        </a>
        <a
          v-if="tool.github"
          :href="tool.github"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center gap-1.5 px-3 py-1.5 rounded border border-catppuccin-surface/60 text-xs text-catppuccin-subtle transition-colors hover:bg-catppuccin-surface/30 hover:text-catppuccin-text"

        >
          <svg class="w-3 h-3" fill="currentColor" viewBox="0 0 24 24">
            <path d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z" />
          </svg>
          GitHub
        </a>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card:hover {
  border-color: color-mix(in srgb, var(--accent-color) 40%, transparent);
}
</style>

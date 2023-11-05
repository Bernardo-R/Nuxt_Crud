
import type { NuxtLink } from '#build/components';

import type { NuxtLink } from '#build/components';
<template>
    <div>
        <nav class="navbar navbar-expand-lg shadow-sm bg-body-tertiary">
  <div class="container">
    <NuxtLink class="navbar-brand" href="/">Navbar</NuxtLink>
    <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
      <span class="navbar-toggler-icon"></span>
    </button>
    <div class="collapse navbar-collapse" id="navbarNav">
      <ul class="navbar-nav ms-auto mb-2 mb-lg-0">
        <li class="nav-item">
          <NuxtLink class="nav-link active" aria-current="page" href="/">Home</NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link" href="/about">About Us</NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link" href="/contact">Contact</NuxtLink>
        </li>
        <li class="nav-item">
          <NuxtLink class="nav-link" href="/students">Students</NuxtLink>
        </li>
       
      </ul>
    </div>
  </div>
</nav>
    </div>
</template>

<script setup lang="ts">

</script>

<style scoped>

</style>
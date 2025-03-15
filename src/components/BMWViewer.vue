<template>
  <div class="relative w-full h-screen">

    <!-- Sketchfab 3D Model Embed'ı -->
    <div class="sketchfab-embed-wrapper">
      <iframe title="Asucuk özel BMW" width="1900" height="980"
        src="https://sketchfab.com/models/8704e302e4214c849bc607edb294be8a/embed" scrolling="no"
        style='overflow: hidden; width: "1900px"; height: "980px";'></iframe>
    </div>

    <!-- Spotify Embed - Daha kompakt ve yatay -->
    <div class="spotify-embed mt-4 p-4 absolute top-24 w-full">
      <iframe src="https://open.spotify.com/embed/track/6GNoRytYHewXprnDo6cvQn" width="300" <!-- Daha kısa bir genişlik
        -->
        height="80" <!-- Daha kısa bir yükseklik -->
        frameborder="0"
        allowtransparency="true"
        allow="encrypted-media"
        style="border-radius: 8px;"
        ></iframe>
    </div>

    <!-- 3D Model and Information -->
    <div id="canvas-container" class="w-full h-full"></div>
    <div class="absolute top-2 left-1 text-green-500 bg-black p-4 rounded">
      <h2 class="text-xl mb-2">Asucuk için BMW 3D hediyem</h2>
      <p>Mauseni kullanarak hareket ettirebilirsin!</p>
      <p>Scroll ile yakınlaştır/uzaklaştır <3 </p>
    </div>

  </div>
</template>

<script setup>
// Vue script kısmı burada kullanılabilir.
</script>

<style scoped>
/* Sayfanın geri kalan stilini ayarlayın */
</style>

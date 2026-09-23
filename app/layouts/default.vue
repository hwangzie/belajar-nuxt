<template>
  <Header />

  <div class="app-layout">
    <Sidebar />

    <main>
      <slot />
    </main>
  </div>

  <Footer />
</template>
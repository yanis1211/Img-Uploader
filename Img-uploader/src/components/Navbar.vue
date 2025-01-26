<template>
    <nav class="navbar">
        <img src="../assets/Logo.png">
        <div class="logo">Image Uploader
        </div>
    </nav>
</template>

<script>
export default {
    name: 'Navbar'
};
</script>

<style scoped>
.navbar {
    position: fixed;
    top: 0;
    width: 100%;
    background-color: #fff;
    color: #333;
    padding: 10px 20px;
    display: flex;
    align-items: center;
    box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
    z-index: 1000;
}

.logo {
    font-size: 1.5rem;
    font-weight: bold;
}
</style>
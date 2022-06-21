<template>
  <nav class="navbar">
    <div class="wrapper">
      <img src="@/assets/logo.png" alt="" class="logo" />
      <div class="nav-right">
        <a href="#">Get in touch</a>
        <button>
          <div class="menu-row"></div>
          <div class="menu-row"></div>
        </button>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "NavBar",
};
</script>

<style lang="scss" scoped>
.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  z-index: 1000;
  .wrapper {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-inline: auto;
    padding-inline: 1rem;
    max-width: 1600px;
    .logo {
      width: 125px;
    }
    .nav-right {
      display: flex;
      align-items: center;
      a {
        margin-right: 77px;
      }
      button {
        cursor: pointer;
        display: flex;
        flex-direction: column;
        justify-content: space-around;
        align-items: center;
        background-color: transparent;
        border: none;
        width: 39px;
        height: 30px;
        .menu-row {
          width: 100%;
          border-top: 1px solid #fff;
        }
      }
    }
  }
}
</style>

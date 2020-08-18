<template>
  <el-container>
    <el-aside width="200px" style="height: 100vh; background: lightblue;">
      <!-- Aside content -->
      <el-menu
        mode="vertical"
        style="height: 100vh;"
        :default-active="$route.path"
        router
      >
        <el-submenu
          v-for="(item, index) in menu.items"
          :key="`menu-item-${index}`"
          :index="index + '1'"
        >
          <template slot="title">{{ item.title }}</template>
          <el-menu-item
            v-for="(subItem, subIndex) in item.items"
            :key="`menu-item-${index}-${subIndex}`"
            :index="subItem.path"
          >
            {{ subItem.title }}
          </el-menu-item>
        </el-submenu>
      </el-menu>
    </el-aside>
    <el-container>
      <el-header height="50px" style="background: lightpink;">
        <!-- Header content -->
      </el-header>
      <el-main style="padding：10px 10px;">
        <!-- Main content -->
        <Nuxt />
      </el-main>
    </el-container>
  </el-container>
</template>

<script>
export default {
  data() {
    return {
      menu: {
        items: [
          {
            title: '内容管理',
            items: [
              { title: '首页', path: '/' },
              { title: '文章管理', path: '/users/usersList' },
            ],
          },
          {
            title: '运营管理',
            items: [{ title: '用户管理', path: '/users/usersList' }],
          },
        ],
      },
    }
  },
}
</script>
<style>
html {
  font-family: 'Source Sans Pro', -apple-system, BlinkMacSystemFont, 'Segoe UI',
    Roboto, 'Helvetica Neue', Arial, sans-serif;
  font-size: 16px;
  word-spacing: 1px;
  height: 100%;
  -ms-text-size-adjust: 100%;
  -webkit-text-size-adjust: 100%;
  -moz-osx-font-smoothing: grayscale;
  -webkit-font-smoothing: antialiased;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: border-box;
  margin: 0;
}

.el-main {
  padding: 10px;
}

.button--green {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #3b8070;
  color: #3b8070;
  text-decoration: none;
  padding: 10px 30px;
}

.button--green:hover {
  color: #fff;
  background-color: #3b8070;
}

.button--grey {
  display: inline-block;
  border-radius: 4px;
  border: 1px solid #35495e;
  color: #35495e;
  text-decoration: none;
  padding: 10px 30px;
  margin-left: 15px;
}

.button--grey:hover {
  color: #fff;
  background-color: #35495e;
}
</style>

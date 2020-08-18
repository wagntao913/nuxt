<template>
  <div>
    USERLIST PAGE
    <el-table :data="dataTable" border stripe>
      <el-table-column
        v-for="col in columns"
        :key="col.id"
        :align="col.align"
        :prop="col.prop"
        :label="col.label"
        :width="col.width"
      >
        <template slot-scope="scope">
          <el-avatar
            v-if="col.prop === 'avatar'"
            :src="scope.row.avatar"
          ></el-avatar>
          <span v-if="col.prop !== 'avatar'">{{ scope.row[col.prop] }}</span>
        </template>
      </el-table-column>
      <el-table-column label="操作" width="180" align="center">
        <template slot-scope="scope">
          <el-button type="text" color="" @click="editClick(scope.row)"
            >修改</el-button
          >
          <el-button type="text" color="" @click="deleteClick(scope.row)"
            >删除</el-button
          >
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  asyncData({
    app,
    isDev,
    route,
    store,
    env,
    params,
    query,
    req,
    res,
    redirect,
    error,
  }) {
    return app.$axios.$get('/users').then((res) => {
      // eslint-disable-next-line no-console
      console.log(res)
      if (res) {
        return { dataTable: res.data }
      }
    })
  },
  data() {
    return {
      dataTable: [],
      columns: [
        { id: '1', align: 'center', label: '用户名', prop: 'username' },
        { id: '2', align: 'center', label: '密码', prop: 'password' },
        { id: '3', align: 'center', label: '头像', prop: 'avatar' },
        { id: '4', align: 'center', label: '创建时间', prop: 'createdAt' },
      ],
    }
  },
  methods: {
    editClick() {
      // eslint-disable-next-line no-console
      console.log('== updateClick ==')
    },
    deleteClick() {
      // eslint-disable-next-line no-console
      console.log('== deleteClick ==')
    },
  },
}
</script>

<style lang="sass" scoped></style>

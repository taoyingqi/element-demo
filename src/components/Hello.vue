<template>
  <div class="hello">
    <el-table :data="users" border style="width: 100%">
      <el-table-column prop="id" label="id" fixed></el-table-column>
      <el-table-column prop="name" label="name"></el-table-column>
      <el-table-column prop="level" label="level"></el-table-column>
      <el-table-column prop="createdAt" label="createdAt"></el-table-column>
      <el-table-column
        fixed="right"
        label="operator"
        width="200">
        <template scope="scope">
          <el-select v-model="levels[scope.$index]" @change="handleChange(scope.$index, scope.row)" placeholder="请选择">
            <el-option
              v-for="(level, index) in levelOptions"
              :key="scope.$index + '-' + index"
              :label="level.label"
              :value="level.value">
            </el-option>
          </el-select>
        </template>
      </el-table-column>
    </el-table>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      levels: [null, null, null, null],
      levelOptions: [
        {
          label: 'common',
          value: 'common'
        }, {
          label: 'vip',
          value: 'vip'
        }, {
          label: 'super',
          value: 'super'
        }
      ],
      users: [
        {
          id: '10000',
          name: 'derfu',
          level: 'common',
          createdAt: '2017-03-23'
        }, {
          id: '10001',
          name: 'bob',
          level: 'vip',
          createdAt: '2017-03-29'
        }, {
          id: '10002',
          name: 'tom',
          level: 'super',
          createdAt: '2017-04-01'
        }, {
          id: '10004',
          name: 'yuri',
          level: 'super',
          createdAt: '2017-04-01'
        }
      ]
    }
  },
  methods: {
    handleChange (index, row) {
      console.log(index, row.id)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>

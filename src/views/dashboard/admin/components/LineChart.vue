<template>
  <el-table
    :data="tableData"
    style="width: 30%"
  >
    <el-table-column
      type="index"
      label="排名"
      width="100"
    />
    <el-table-column
      prop="name"
      label="领域"
      width="100"
    />
    <el-table-column
      prop="address"
      label="占比"
    >
      <template slot-scope="scope">
        <el-progress :percentage="scope.row.address" />
      </template>
    </el-table-column>

  </el-table>
</template>

<script>
export default {
  data() {
    return {
      tableData: [{
        name: '应急救援',
        address: 30
      }, {
        name: '应急救护',
        address: 50
      }, {
        name: '人道救助',
        address: 40
      }, {
        name: '造血干细胞捐献',
        address: 70
      }, {
        name: '人体器官（遗体、组织）捐献',
        address: 8
      }, {
        name: '无偿献血',
        address: 78
      }, {
        name: '红十字文化传播',
        address: 60
      }
      ]
    }
  },
  mounted() {
    const compare = function(obj1, obj2) {
      const var1 = obj1.address
      const var2 = obj2.address
      if (var2 < var1) {
        return -1
      } else if (var2 > var1) {
        return 1
      } else {
        return 0
      }
    }
    this.tableData.sort(compare)
  },
  methods: {
    format(percentage) {
      return percentage === 100 ? '满' : `${percentage}%`
    }
  }

}
</script>

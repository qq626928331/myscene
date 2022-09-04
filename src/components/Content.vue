<template>
    <el-container>
        <el-header>
            <h1>我的场景</h1>
        </el-header>
        <el-container>
            <el-aside>
                <el-tree :data="data" :props="defaultProps" accordion @node-click="handelNodeClick">
                </el-tree>
            </el-aside>
            <el-container>
                <el-header>
                    场景名称：
                </el-header>
                <el-main>
                    <div style="text-align:left;margin-top: 0;">
                        <el-button :disabled="isEdit">添加条件</el-button>
                        <el-button :disabled="isEdit">删除条件</el-button>
                        <el-table ref="multipleTable" :data="tableData" tooltip-effect="dark" style="width: 100%"
                            @selection-change="handleSelectionChange">
                            <el-table-column type="selection" width="55">
                            </el-table-column>
                            <el-table-column label="日期" width="120">
                                <template slot-scope="scope">{{ scope.row.date }}</template>
                            </el-table-column>
                            <el-table-column prop="name" label="姓名" width="120">
                            </el-table-column>
                            <el-table-column prop="address" label="地址" show-overflow-tooltip>
                            </el-table-column>
                        </el-table>
                    </div>

                    main
                </el-main>
                <el-footer>
                    <el-button @click="handelEdit">修改</el-button>
                    <el-button>修改</el-button>
                    <el-button :disabled="isEdit" @click="handelSave">保存</el-button>
                    <el-button :disabled="isEdit" @click="handelCancel">取消</el-button>
                </el-footer>
            </el-container>
        </el-container>
    </el-container>
</template>

<script>
export default {
    name: "ContentsComponet",
    data(){
        return{
            data: [{
          label: '一级 1',
          children: [{
            label: '二级 1-1',
            children: [{
              label: '三级 1-1-1'
            }]
          }]
        }, {
          label: '一级 2',
          children: [{
            label: '二级 2-1',
            children: [{
              label: '三级 2-1-1'
            }]
          }, {
            label: '二级 2-2',
            children: [{
              label: '三级 2-2-1'
            }]
          }]
        }, {
          label: '一级 3',
          children: [{
            label: '二级 3-1',
            children: [{
              label: '三级 3-1-1'
            }]
          }, {
            label: '二级 3-2',
            children: [{
              label: '三级 3-2-1'
            }]
          }],
        }],
        defaultProps: {
          children: 'children',
          label: 'label'
        },
        isEdit: true,
        tableData: [{
          date: '2016-05-03',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-02',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-04',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-01',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-08',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-06',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }, {
          date: '2016-05-07',
          name: '王小虎',
          address: '上海市普陀区金沙江路 1518 弄'
        }],
        multipleSelection: []
      };
        
    },
    methods: {
      handleNodeClick(data) {
        console.log(data);
      },
      handelEdit(){
          this.isEdit = false;
      },
      toggleSelection(rows) {
        if (rows) {
          rows.forEach(row => {
            this.$refs.multipleTable.toggleRowSelection(row);
          });
        } else {
          this.$refs.multipleTable.clearSelection();
        }
      },
      handleSelectionChange(val) {
        this.multipleSelection = val;
      },
      handelCancel(){
        this.isEdit = true;
      },
      handelSave(){
        this.isEdit = true;
      }
    }
    
}
</script>

<style>
.el-header,
.el-footer {
    background-color: #B3C0D1;
    color: #333;
    /* text-align: center; */
    line-height: 60px;
}

.el-aside {
    background-color: #D3DCE6;
    color: #333;
    /* text-align: center; */
    line-height: 200px;
}

.el-main {
    background-color: #E9EEF3;
    color: #333;
    /* text-align: center; */
    /* line-height: 160px; */
}

body>.el-container {
    margin-bottom: 40px;
}

.el-container:nth-child(5) .el-aside,
.el-container:nth-child(6) .el-aside {
    line-height: 260px;
}

.el-container:nth-child(7) .el-aside {
    line-height: 320px;
}
</style>
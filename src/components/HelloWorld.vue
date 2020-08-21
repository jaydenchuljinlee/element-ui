<template>
  <div class="hello">
    <el-container>
      <el-row>
        <el-col :span="24">
          <div class="grid-content bg-purple-dark">
            <el-button-group>
              <el-button typeof="primary" icon="el-icon-edit" />
              <el-button typeof="primary" icon="el-icon-share" />
              <el-button typeof="primary" icon="el-icon-delete" />
            </el-button-group><br />

            <el-radio-group v-model="radio2">
              <el-radio :label="3">Option A</el-radio>
              <el-radio :label="6">Option B</el-radio>
              <el-radio :label="9">Option C</el-radio>
            </el-radio-group><br />

            <el-radio-group v-model="radio3">
              <el-radio-button label="New York"></el-radio-button>
              <el-radio-button label="Washington"></el-radio-button>
              <el-radio-button label="Los Angeles"></el-radio-button>
              <el-radio-button label="Chicago"></el-radio-button>
            </el-radio-group><br />

            <el-radio-group v-model="radio4">
              <el-radio v-model="radio7" label="1" border>Option A</el-radio>
              <el-radio v-model="radio7" label="2" border>Option A</el-radio>
            </el-radio-group><br />

            <el-select v-model="value" placeholder="Select">
              <el-option v-for="item in options"
                         :key="item.value"
                         :label="item.label"
                         :value="item.value">
              </el-option>
            </el-select>

            <el-table :data="tableData"
                      style="width: 100%">
              <el-table-column prop="date"
                               label="Date"
                               width="180">
              </el-table-column>
              <el-table-column prop="name"
                               label="Name"
                               width="180">
              </el-table-column>
              <el-table-column prop="name"
                               label="Name"
                               width="180">
              </el-table-column>
            </el-table>

            <el-tree :data="data3"
                     :props="defaultProps"
                     show-checkbox
                     @check-change="handleCheckChange">
            </el-tree>

            <el-tabs v-model="activeName" @tab-click="handleClick">
              <el-tab-pane label="User" name="first">user</el-tab-pane>
              <el-tab-pane label="Config" name="second">Config</el-tab-pane>
              <el-tab-pane label="Role" name="third">Role</el-tab-pane>
              <el-tab-pane label="Task" name="fourth">Task</el-tab-pane>
            </el-tabs>

            <el-tooltip content="Top center" placement="top">
              <el-button>Dark</el-button>
            </el-tooltip>
            <el-tooltip content="Bottom center" placement="bottom" effect="light">
              <el-button>Light</el-button>
            </el-tooltip>

            <el-date-picker v-mode="value1"
                            type="datetime"
                            placeholder="Select date and time">
            </el-date-picker>

            <el-progress :text-inside="true" :stroke-width="18" :percentage="0"></el-progress>
            <el-progress :text-inside="true" :stroke-width="18" :percentage="70"></el-progress>
            <el-progress :text-inside="true" :stroke-width="18" :percentage="100" status="success"></el-progress>
            <el-progress :text-inside="true" :stroke-width="18" :percentage="0" status="exception"></el-progress>

            <el-upload class="upload-demo"
                       action="https://jsonplaceholder.typicode.com/posts/"
                       :on-preview="handlePriview"
                       :on-remove="handleRemove"
                       :before-remove="beforeRemove"
                       multiple
                       :limit="3"
                       :on-excees="handleExceed"
                       :file-list="fileList">
              <el-button size="small" typeof="primary">Click to upload</el-button>
              <div slot="tip" class="el-upload__tip">jpg/png files with a size less than 500kb</div>
            </el-upload>

            <el-menu :default-active="activeIndex2"
                     class="el-menu-demo"
                     mode="horizontal"
                     @select="handleSelect"
                     background-color="#545c64"
                     text-color="#fff"
                     active-text-color="#ffd04b">
              <el-menu-item index="1">Processing Center</el-menu-item>
              <el-submenu index="2">
                <template slot="title">
                  Workspace
                </template>
                <el-menu-item index="2-1">item one</el-menu-item>
                <el-menu-item index="2-2">item two</el-menu-item>
                <el-menu-item index="2-3">item three</el-menu-item>
                <el-submenu index="2-4">
                  <template slot="title">
                    item four
                  </template>
                  <el-menu-item index="2-4-1">item one</el-menu-item>
                  <el-menu-item index="2-4-2">item two</el-menu-item>
                  <el-menu-item index="2-4-3">item three</el-menu-item>
                </el-submenu>
              </el-submenu>
              <el-menu-item index="3" disabled>Info</el-menu-item>
              <el-menu-item index="4"><a href="https://www.ele.me" target="_blank">Orders</a></el-menu-item>
            </el-menu>

            <el-alert title="success alert"
                      type="success"></el-alert>

            <el-dialog title="Tips"
                       :visible.sync="dialogVisible"
                       width="30%"
                       :before-close="handleClose">
              <span>This is a message</span>
              <span slot="footer" class="dialog-footer">
                <el-button @click="dialogVisible=false">Cancle</el-button>
                <el-button type="primary" @click="dialogVisible=false">Confirm</el-button>
              </span>
            </el-dialog>

            <el-pagenation
                           background
                           layout="prev, page, next"
                           :total="1000"></el-pagenation>
          </div>
        </el-col>
      </el-row>
    </el-container>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      options: [{
        value: 'Option1',
        label: 'Option1'
      }, {
        value: 'Option2',
        label: 'Option2'
      }, {
        value: 'Option3',
        label: 'Option3'
      }],
      value: '',
      tableData: [{
        date: '2016-05-03',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-04',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-01',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }],
      data3: [{
        id: 1,
        label: 'Level one 1',
        children: [{
          id: 3,
          label: 'Level two 2-1',
          children: [{
            id: 4,
            label: 'Level three 3-1-1'
          }, {
            id: 5,
            label: 'Level three 3-1-2',
            disabled: true
          }]
        }]
      }],
      activeName: 'first'
    }
  },
  methods: {
    handleClick(tab, event) {
      console.log(tab, event)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>

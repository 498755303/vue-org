<template>
  <div>
    <button @click.stop="remove">删除节点</button>
    <button @click.stop="append">增加节点</button>
    <button @click.stop="insertBefore">节点前增加</button>
    <button @click.stop="insertAfter">节点后增加</button>

    <demo :data="demoData"
          ref="orgTree"
          :collapsable="true"
          :horizontal="true"
          :defaultExpandAll="true"
          :expandOnClickNode="true"
          :selectOnClickNode="false"
          :renderContent="renderContent"
          selectedKey="id"
          selectedClassName="select-node"
          @expand-change="expendHandle"
          @node-contextmenu="nodeContextmenu"></demo>
  </div>
</template>
<script>
import demo from "../packages/org/index";
export default {
  props: {},
  data() {
    return {
      demoData: {
        id: 1,
        label: "1",
        companyName: "xx科技有限公司",
        userName: "某某",
        expand: true,
        children: [
          {
            id: 11,
            label: "1-1",
            expand: false,
            children: [
              {
                id: 111,
                label: "1-1",
                expand: true
              }
            ]
          },
          {
            id: 12,
            label: "1-2",
            expand: false,
            children: [
              {
                id: 121,
                label: "1-2-1",
                expand: false
              },
              {
                id: 122,
                label: "1-2-2",
                expand: false
              }
            ]
          }
        ]
      }
    };
  },
  computed: {},
  methods: {
    expendHandle(e, data) {
      // this.$set(data, 'expand', !data.expand);
    },
    remove() {
      this.$refs.orgTree.getSelectedNode();
      this.$refs.orgTree.removeNode(11);
    },
    append() {
      this.$refs.orgTree.appendNode(
        {
          id: 13,
          label: "1-3",
          expand: true
        },
        1
      );
    },
    insertBefore() {
      this.$refs.orgTree.insertBefore(
        {
          id: 10,
          label: "1-0",
          expand: true
        },
        11
      );
    },
    insertAfter() {
      this.$refs.orgTree.insertAfter(
        {
          id: 999,
          label: "1-1.5",
          expand: true
        },
        11
      );
    },
    nodeContextmenu(e, data) {
      console.log(data);
    },
    editLeader(e, data) {
      console.log(e, data);
    },
    renderContent(h, data) {
      return h(
        "div",
        {
          domProps: {
            className: "org-label-self"
          }
        },
        [
          h("p", {
            domProps: {
              className: "company-name",
              innerText: data.companyName || "-"
            }
          }),
          h("span", {
            domProps: {
              className: "company-leader",
              innerHTML: data.userName || "-"
            }
          }),
          h("span", {
            domProps: {
              className: "el-icon-edit",
              innerText: "测试按钮"
            },
            on: {
              click: e => this.editLeader(e, data)
            }
          }),
          h("div", {
            domProps: {
              className: "org-popover",
              innerText: "悬浮窗"
            }
          })
        ]
      );
    }
  },
  components: {
    demo
  },
  created() {}
};
</script>
<style scoped lang="less">
@deep: ~">>>";
@{deep} .select-node {
  border: 1px solid #409eff !important;
}

button {
  margin: 0 20px;
  border-color: #409eff;
}
</style>

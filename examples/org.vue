<template>
  <div class="demo-org">
    <div class="org-wrap">
      <div class="org-tree horizontal">
        <div class="org-node">
          <div class="org-label">
            <div class="org-label-inner">
              <div class="label-content">
                <div class="label-title">xx</div>
                <div class="intro">
                  <span>某某某</span>
                  <span>成员</span>
                </div>
              </div>
            </div>

            <div class="operate-button">
            </div>
          </div>
          <div class="org-children">
            <div class="org-node ">
              <div class="org-label">
                <div class="org-label-inner">
                  <div class="label-content">
                    <p class="label-title">xx</p>
                    <div class="intro">
                      <span>某某某</span>
                      <span>成员</span>
                    </div>
                  </div>
                  <div class="operate-button">
                  </div>
                </div>
              </div>
              <div class="org-children">
                <div class="org-node leaf">
                  <div class="org-label">
                    <div class="org-label-inner">
                      <div class="label-content">
                        <p class="label-title">xx</p>
                        <div class="intro">
                          <span>某某某</span>
                          <span>成员</span>
                        </div>
                      </div>
                    </div>
                  </div>
                </div>
              </div>
            </div>
            <div class="org-node collapsed">
              <div class="org-label">
                <div class="org-label-inner">
                  <div class="label-content">
                    <p class="label-title">xx</p>
                    <div class="intro">
                      <span>某某某</span>
                      <span>成员</span>
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {},
  data() {
    return {};
  },
  computed: {},
  methods: {},
  components: {},
  created() {}
};
</script>
<style scoped lang="less">
@btnColor: #0000ff;
@buttonInnerColor: #fff;
@lineColor: #0000ff;
@childPadTop: 30px;
@nodePadTop: 20px;
.org-wrap {
  display: inline-block;
  .org-tree {
    text-align: center;
    display: table;
    .org-node {
      position: relative;
      display: table-cell;
      padding-top: @nodePadTop;
      box-sizing: border-box;
      &.leaf {
        padding-left: 15px;
        padding-right: 15px;
        box-sizing: border-box;
      }
      &.collapsed {
        padding-left: 15px;
        padding-right: 15px;
        box-sizing: border-box;
      }
      .org-label {
        position: relative;
        display: inline-block;
        vertical-align: middle;
        .org-label-inner {
          box-shadow: 0 2px 12px 0 rgba(0, 0, 0, 0.1);
          padding: 5px 15px;
          box-sizing: border-box;
          .operate-button {
            position: absolute;
            border-radius: 50%;
            display: block;
            width: 20px;
            height: 20px;
            padding: 2px;
            box-sizing: border-box;
            background-color: @btnColor;
            bottom: 0;
            left: 50%;
            transform: translate(-50%, 50%);
            cursor: pointer;
            z-index: 2;
            &:before {
              position: absolute;
              top: 50%;
              transform: translate(0, -50%);
              display: block;
              content: "";
              width: 80%;
              height: 2px;
              background-color: #fff;
            }
            &.expanded:after {
              position: absolute;
              left: 50%;
              transform: translate(-50%, 0);
              display: block;
              content: "";
              width: 2px;
              height: 80%;
              background-color: #fff;
            }
          }
          // 以下不如组件
          .label-title {
            line-height: 30px;
          }
          span {
            margin: 0 15px;
          }
        }
      }
      .org-children {
        display: table;
        position: relative;
        padding-top: @childPadTop;
        &:before {
          position: absolute;
          top: 0;
          left: 50%;
          display: block;
          content: "";
          width: 1px;
          height: @childPadTop;
          background-color: @lineColor;
        }
      }
      &:before {
        position: absolute;
        display: block;
        content: "";
        top: 0;
        left: 0;
        width: 50%;
        height: calc(@nodePadTop - 1px);
      }
      &:after {
        position: absolute;
        display: block;
        content: "";
        top: 0;
        left: 50%;
        width: 50%;
        height: calc(@nodePadTop - 1px);
        border-left: 1px solid @lineColor;
      }
      &:not(:first-child):before {
        border-top: 1px solid @lineColor;
      }
      &:not(:last-child):after {
        border-top: 1px solid @lineColor;
      }
    }
  }
  .org-tree > .org-node:after {
    border-left: 0;
  }
  .org-tree.horizontal > .org-node:after {
    border-top: 0 !important;
  }

  .org-tree.horizontal {
    .org-node {
      display: table;
      padding-top: 0;
      padding-left: @nodePadTop;
      .org-label {
        display: table-cell;
        .operate-button {
          position: absolute;
          border-radius: 50%;
          display: block;
          width: 20px;
          height: 20px;
          padding: 2px;
          box-sizing: border-box;
          background-color: @btnColor;
          left: 100%;
          bottom: 50%;
          transform: translate(-50%, 50%);
          cursor: pointer;
          z-index: 2;
        }
      }
      .org-children {
        display: table-cell;
        padding-top: 0;
        padding-left: @childPadTop;
        &:before {
          position: absolute;
          top: 50%;
          left: 0;
          display: block;
          content: "";
          width: @childPadTop;
          height: 1px;
          background-color: @lineColor;
        }
      }
      &.leaf {
        padding: 15px 0 15px 20px;
        box-sizing: border-box;
      }
      &.collapsed {
        padding: 15px 0 15px 20px;
        box-sizing: border-box;
      }
      &:before {
        width: calc(@nodePadTop - 1px);
        height: 50%;
      }
      &:after {
        top: 50%;
        left: 0;
        width: calc(@nodePadTop - 1px);
        height: 50%;
        border-top: 1px solid @lineColor;
        border-left: 0;
      }
      &:not(:first-child):before {
        border-left: 1px solid @lineColor;
        border-top: 0;
      }
      &:not(:last-child):after {
        border-left: 1px solid @lineColor;
      }
    }
  }
}
</style>

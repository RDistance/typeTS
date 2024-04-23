<template>
  <div class="comments-wrap">
    <h3 class="title">评价</h3>
    <div class="top-type">
      <span v-for="(type, index) in types" :key="index" @click="onGetComments(type)"
        :class="{ active: type === currentShow }">{{ type }}</span>
    </div>
    <div class="comments-content">
      <div class="comments" v-show="currentShow === '全部'">
        <CommentContent :comments="allComments" />
      </div>
      <div class="comments" v-show="currentShow === '有图/视频'">
        <CommentContent :comments="picComments" />
      </div>
      <div class="comments" v-show="currentShow === '追评'">
        <CommentContent :comments="followComments" />
      </div>
    </div>
  </div>
</template>

<script>
import CommentContent from "@/components/file/comment-content";
export default {
  components: {
    CommentContent
  },
  data() {
    return {
      types: ["全部", "有图/视频", "追评"],
      currentShow: "全部",
      allComments: [
        {
          name: "haha",
          time: "5个月前",
          paperType: "大学生版",
          comment: "非常好用",
          pictures: ["avatar.jpg", "avatar.jpg", "avatar.jpg"],
          viewsNum: 2470,
          addComment: "论文通过啦",
          addTime: "29天后",
          addpictures: ["avatar.jpg", "avatar.jpg"]
        },
        {
          name: "xixi",
          time: "3个月前",
          paperType: "编辑部版",
          comment: "此用户没有填写评价。",
          viewsNum: 1000,
          addComment: "论文通过啦",
          addTime: "30天后",
          addpictures: []
        },
      ],
      picComments: [
        {
          name: "haha",
          time: "5个月前",
          paperType: "大学生版",
          comment: "非常好用",
          pictures: ["avatar.jpg", "avatar.jpg", "avatar.jpg"],
          viewsNum: 2470,
          addComment: "",
          addTime: "",
          addpictures: []
        },
        {
          name: "haha",
          time: "5个月前",
          paperType: "大学生版",
          comment: "非常好用",
          pictures: ["avatar.jpg"],
          viewsNum: 2470,
          addComment: "论文通过啦",
          addTime: "29天后",
          addpictures: ["avatar.jpg", "avatar.jpg"]
        },
      ],
      followComments: [
        {
          name: "xixi",
          time: "6个月前",
          paperType: "研究生版",
          comment: "非常好用",
          pictures: ["avatar.jpg", "avatar.jpg", "avatar.jpg"],
          viewsNum: 1000,
          addComment: "论文通过啦",
          addTime: "30天后",
          addpictures: ["avatar.jpg"]
        },
        {
          name: "xixi",
          time: "3个月前",
          paperType: "编辑部版",
          comment: "此用户没有填写评价。",
          viewsNum: 2000,
          addComment: "论文通过啦",
          addTime: "30天后",
          addpictures: []
        },
      ],
    };
  },
  methods: {
    onGetComments(type) {
      this.currentShow = type;
    },
  },
};
</script>

<style lang="less" scoped>
.comments-wrap {
  margin-top: 30px;

  .title {
    color: #000;
    font-weight: 600;
  }

  .top-type {
    margin-bottom: 24px;

    span {
      display: inline-block;
      margin-right: 12px;
      height: 36px;
      line-height: 20px;
      border-radius: 18px;
      padding: 8px 16px;
      background-color: #f6f6f6;
      color: #333;
      font-size: 14px;
      cursor: pointer;
      position: relative;
      transition: all .1s linear;

      &.active {
        background-color: #ff5000;
        color: #fff;
      }
    }
  }
}
</style>

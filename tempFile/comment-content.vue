<template>
    <div class="comment-content-wrap">
        <div class="comment-content" v-for="(item, index) in comments" :key="index">
            <div class="header">
                <div class="avatar">
                    <img src="@/assets/avatar.jpg">
                </div>
                <div class="user-info">
                    <div class="userName">{{ item.name }}</div>
                    <div class="meta">
                        <span class="time">{{ item.time }}</span>
                        <span>{{ item.paperType }}</span>
                    </div>
                </div>
            </div>
            <div class="content">
                <div class="remark">{{ item.comment }}</div>
                <div class="album">
                    <div class="album-item" v-for="(pic, i) in item.pictures" :key="i">
                        <img :src="require(`../../assets/${pic}`)">
                    </div>
                </div>
            </div>
            <div class="append" v-show="item.addComment || item.addpictures.length > 0">
                <div class="remark">
                    <span class="time">{{ item.addTime }}追评</span>
                    <span>{{ item.addComment }}</span>
                </div>
                <div class="album">
                    <div class="album-item" v-for="(pic, i) in item.addpictures" :key="i">
                        <img :src="require(`../../assets/${pic}`)">
                    </div>
                </div>
            </div>
            <div class="footer">
                浏览<span>{{ item.viewsNum }}</span>次
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: {
        comments: {
            type: Array,
            default() {
                return [];
            }
        }
    },
    data() {
        return {}
    },
    methods: {

    },
};
</script>


<style lang="less" scoped>
.comment-content-wrap {
    .comment-content {
        margin-bottom: 18px;

        .header {
            display: flex;

            .avatar {
                img {
                    height: 36px;
                    width: 36px;
                    border-radius: 18px;
                    line-height: 39px;
                }
            }

            .user-info {
                margin-left: 7px;

                .userName {

                    font-weight: 700;
                    font-size: 17px;
                    color: #000;
                    line-height: 22px;
                }

                .meta {
                    font-size: 14px;
                    color: #7a7a7a;
                    line-height: 18px;

                    .time {
                        margin-right: 5px;
                    }
                }
            }
        }

        .content {
            margin-top: 15px;
            padding-top: 0;

            .remark {
                font-size: 16px;
                color: #000;
                line-height: 22px;
            }
        }

        .album {
            display: flex;
            flex-wrap: wrap;
            margin-top: 7px;

            .album-item {
                height: 100px;
                width: 100px;
                margin-right: 4px;
                margin-bottom: 4px;
                cursor: pointer;

                img {
                    width: 100%;
                    height: 100%;
                }

                &:first-child {
                    img {
                        border-top-left-radius: 12px;
                        border-bottom-left-radius: 12px;
                    }
                }

                &:last-child {
                    img {
                        border-top-right-radius: 12px;
                        border-bottom-right-radius: 12px;
                    }
                }
            }
        }

        .append {
            background-color: rgba(0, 0, 0, .02);
            padding: 12px;
            border-radius: 12px;
            margin-top: 12px;

            .remark {
                font-size: 16px;
                color: #000;
                line-height: 22px;

                .time {
                    color: #ff5000;
                    margin-right: 12px;
                }
            }

            .album {
                margin-bottom: 12px;
            }
        }

        .footer {
            margin-top: 14px;
            font-size: 13px;
            line-height: 18px;
            color: #7a7a7a;
        }
    }
}
@media screen and (max-width:750px){
    .comment-content-wrap {
        .comment-content {
            .album {
                .album-item {
                    width: 80px;
                    height: 80px;
                } 
            }
        }
    } 
}
</style>
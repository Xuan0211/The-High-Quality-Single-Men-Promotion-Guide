<script>
    export default {
        onLaunch: function() {
            console.log('App Launch')
        },
        onShow: function() {
            console.log('App Show')
        },
        onHide: function() {
            console.log('App Hide')
        }
    }
</script>

<style>
    /************************************************************
** 请将全局样式拷贝到项目的全局 CSS 文件或者当前页面的顶部 **
** 否则页面将无法正常显示                                  **
************************************************************/

    html {
        font-size: 16px;
    }

    body {
        margin: 0;
        font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 'Oxygen', 'Ubuntu', 'Cantarell', 'Fira Sans',
            'Droid Sans', 'Helvetica Neue', 'Microsoft Yahei', sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
    }

    view,
    image,
    text {
        box-sizing: border-box;
        flex-shrink: 0;
    }

    #app {
        width: 100vw;
        height: 100vh;
    }

    .flex-row {
        display: flex;
        flex-direction: row;
    }

    .flex-col {
        display: flex;
        flex-direction: column;
    }

    .justify-start {
        justify-content: flex-start;
    }

    .justify-end {
        justify-content: flex-end;
    }

    .justify-center {
        justify-content: center;
    }

    .justify-between {
        justify-content: space-between;
    }

    .justify-around {
        justify-content: space-around;
    }

    .justify-evenly {
        justify-content: space-evenly;
    }

    .items-start {
        align-items: flex-start;
    }

    .items-end {
        align-items: flex-end;
    }

    .items-center {
        align-items: center;
    }

    .items-baseline {
        align-items: baseline;
    }

    .items-stretch {
        align-items: stretch;
    }

    .self-start {
        align-self: flex-start;
    }

    .self-end {
        align-self: flex-end;
    }

    .self-center {
        align-self: center;
    }

    .self-baseline {
        align-self: baseline;
    }

    .self-stretch {
        align-self: stretch;
    }

    .flex-1 {
        flex: 1 1 0%;
    }

    .flex-auto {
        flex: 1 1 auto;
    }

    .grow {
        flex-grow: 1;
    }

    .grow-0 {
        flex-grow: 0;
    }

    .shrink {
        flex-shrink: 1;
    }

    .shrink-0 {
        flex-shrink: 0;
    }

    .relative {
        position: relative;
    }
</style>
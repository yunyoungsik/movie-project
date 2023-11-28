<template>
    <header id="header" role="banner">
        <a href="">
            <h1 class="logo">
                MP
            </h1>
        </a>
        <nav class="nav">
            <ul>
                <li><a href="#">홈</a></li>
                <li><a href="#">영화TOP10</a></li>
                <li><a href="#">코미디영화 TOP10</a></li>
            </ul>
        </nav>
    </header>
</template>
<style lang="scss">
#header {
    width: 100%;
    height: 100px;
    padding: 1rem;
    display: flex;
    align-items: center;
    position: fixed;
    top: 0;
    z-index: 1000;

    .logo {
        width: 60px;
        height: 60px;
        line-height: 60px;
        font-size: 1rem;
        font-weight: bold;
        text-align: center;
        border-radius: 50%;
        background-color: #F80147;
        margin-right: 5rem;
    }

    .nav {
        ul {
            display: flex;

            li {

                a {
                    margin-right: 2rem;
                    font-size: 1rem;
                    font-weight: bold;

                    &:hover {
                        color: #F80147;
                    }
                }
            }
        }
    }
}
</style>
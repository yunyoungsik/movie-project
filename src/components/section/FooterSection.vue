<template>
    <footer id="footer" role="contentinfo">
        <div class="footer__inner container1280">
            <div class="footer1">
                <a href="#">
                    <h2 class="logo">
                        MP
                    </h2>
                </a>
            </div>
            <div class="footer2">
                <nav class="nav">
                    <ul>
                        <li>
                            <ul>
                                <li><a href=""><a href="#">MENU1</a></a></li>
                                <li><a href=""><a href="#">MENU2</a></a></li>
                                <li><a href=""><a href="#">MENU3</a></a></li>
                                <li><a href=""><a href="#">MENU4</a></a></li>
                            </ul>
                        </li>
                        <li>
                            <ul>
                                <li><a href=""><a href="#">MENU1</a></a></li>
                                <li><a href=""><a href="#">MENU2</a></a></li>
                                <li><a href=""><a href="#">MENU3</a></a></li>
                                <li><a href=""><a href="#">MENU4</a></a></li>
                            </ul>
                        </li>
                        <li>
                            <ul>
                                <li><a href=""><a href="#">MENU1</a></a></li>
                                <li><a href=""><a href="#">MENU2</a></a></li>
                                <li><a href=""><a href="#">MENU3</a></a></li>
                                <li><a href=""><a href="#">MENU4</a></a></li>
                            </ul>
                        </li>
                        <li>
                            <ul>
                                <li><a href=""><a href="#">MENU1</a></a></li>
                                <li><a href=""><a href="#">MENU2</a></a></li>
                                <li><a href=""><a href="#">MENU3</a></a></li>
                                <li><a href=""><a href="#">MENU4</a></a></li>
                            </ul>
                        </li>
                    </ul>
                </nav>
            </div>
            <div class="footer3">
                <h2>Contact noew</h2>
                <input type="text" name="" id="" placeholder="Your e-mail">
                <button>CONTACT</button>
            </div>
            <div class="footerB">
                <div class="footerB__left">
                    <p>Copyright ⓒ 2023 yunyoungsik.All rights reserved.</p>
                    <nav class="nav">
                        <ul>
                            <li><a href="https://github.com/yunyoungsik">GITHUB</a></li>
                            <li><a href="mailto:yunyoungsik91@gmail.com">MAIL</a></li>
                        </ul>
                    </nav>
                </div>
                <div class="footerB__right">
                    <a href="">
                        <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
                            <path
                                d="M12 0c-6.626 0-12 5.373-12 12 0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23.957-.266 1.983-.399 3.003-.404 1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576 4.765-1.589 8.199-6.086 8.199-11.386 0-6.627-5.373-12-12-12z" />
                        </svg>
                    </a>
                </div>
            </div>
        </div>

    </footer>
</template>
<style lang="scss">
#footer {
    width: 100%;
    background-color: #090A0E;
    z-index: 1000;

    .footer__inner {
        padding: 100px 0;
        height: 600px;
        display: flex;
        flex-wrap: wrap;

        .footer1 {
            width: 20%;
            height: 80%;

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
        }

        .footer2 {
            width: 60%;
            height: 80%;

            .nav {
                ul {
                    li {
                        margin-right: 4rem;

                        ul {
                            display: flex;
                        }
                    }
                }
            }
        }

        .footer3 {
            width: 20%;
            height: 80%;
        }

        .footerB {
            width: 100%;

            .footerB__left {
                p {
                    font-size: 0.8rem;
                }

                .nav {
                    ul {
                        display: flex;

                        li {


                            &:first-child {
                                border-right: 1px solid #fff;
                            }

                            a {
                                font-size: 0.8rem;
                                padding: 0 10px;
                            }
                        }
                    }
                }
            }

            .footerB__right {
                a {
                    svg {
                        fill: ;
                    }
                }
            }
        }
    }
}
</style>
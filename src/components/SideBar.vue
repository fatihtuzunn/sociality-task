<template>

    <section class="side">

        <header>

            <img src="../assets/Sociality-logo.png" alt="" class="mt-3">

        </header>


        <div class="sidebar d-flex">



            <div class="d-flex flex-column sideBarFirst flex-shrink-0 " style="width: 77px;">


                <ul class="nav nav-pills nav-flush flex-column mb-auto text-center">


                    <li @click="activeToggle" class="nav-link">
                        <img src="../assets/Logo4.png" style="cursor:pointer"  >

                    </li>
                    <li @click="activeToggle" class="nav-link">

                        <img src="../assets/Logo4.png" style="cursor:pointer"  >

                    </li>
                    <li @click="activeToggle" class="nav-link active">
                        <img src="../assets/Logo4.png" style="cursor:pointer"  >

                    </li>
                    <li @click="activeToggle" class="nav-link">
                        <img src="../assets/Logo4.png" style="cursor:pointer"  >

                    </li>
                    <li @click="activeToggle" class="nav-link">
                        <img src="../assets/Logo4.png" style="cursor:pointer"  >

                    </li>
                </ul>

            </div>


            <div class="flex-shrink-0 sideBarSec text-start" style="width: 211px;">

                <ul class="list-unstyled ps-0 ">
                    <li class="mb-1">
                        <div class="btntext">
                            <h5><span><i class="bi bi-bell text-center"></i></span>Notifications</h5>
                        </div>
                    </li>

                    <li class="mb-1">
                        <button class="btn btn-toggle rounded collapsed justify-content-start" @click="collapseOpen"
                            data-bs-toggle="collapse" data-bs-target="#home-collapse" aria-expanded="false">
                            <div class="btntext">


                                <h5><span><i class="bi bi-graph-up-arrow"></i></span>summary</h5>
                                <div class="plus-button">
                                    <div class="plus-icon"></div>
                                </div>
                            </div>

                        </button>
                        <div class="collapse" id="home-collapse">
                            <ul class="btn-toggle-nav  fw-normal pb-1 small text-light">
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Overview</a></li>
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Updates</a></li>
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Reports</a></li>
                            </ul>
                        </div>
                    </li>
                    <li class="mb-1">
                        <button class="btn btn-toggle  rounded collapsed" data-bs-toggle="collapse"
                            @click="collapseOpen" data-bs-target="#dashboard-collapse" aria-expanded="false">
                            <div class="btntext">
                                <h5> <span><i class="bi bi-pencil-square"></i></span> Publish</h5>
                                <div class="plus-button" :class="{open: open}">
                                    <div class="plus-icon"></div>
                                </div>
                            </div>
                        </button>
                        <div class="collapse" id="dashboard-collapse" style="">
                            <ul class="btn-toggle-nav  fw-normal pb-1 small text-light">
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Compose</a></li>
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Feed</a></li>
                                
                            </ul>
                        </div>
                    </li>
                    <li class="mb-1">
                        <button class="btn btn-toggle  rounded collapsed" data-bs-toggle="collapse"
                            @click="collapseOpen" data-bs-target="#orders-collapse" aria-expanded="false">
                            <div class="btntext">
                                <h5> <span><i class="bi bi-chat-left-text-fill"></i></span> Engage </h5>
                                <div class="plus-button" :class="{open: open}">
                                    <div class="plus-icon"></div>
                                </div>
                            </div>
                        </button>
                        <div class="collapse" id="orders-collapse" style="">
                            <ul class="btn-toggle-nav  fw-normal pb-1 small text-light">
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">New</a></li>
                                
                            </ul>
                        </div>
                    </li>
                    <li class="mb-1">
                        <button class="btn btn-toggle  rounded collapsed" data-bs-toggle="collapse"
                            @click="collapseOpen" data-bs-target="#account-collapse" aria-expanded="false">
                            <div class="btntext">
                                <h5> <span><i class="bi bi-activity"></i></span> Listen</h5>
                                <div class="plus-button" :class="{open: open}">
                                    <div class="plus-icon"></div>
                                </div>
                            </div>
                        </button>
                        <div class="collapse" id="account-collapse" style="">
                            <ul class="btn-toggle-nav fw-normal pb-1 small text-light ">
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">New...</a></li>
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Report</a></li>
                                
                            </ul>
                        </div>
                    </li>
                    <li class="mb-1">
                        <button class="btn btn-toggle  rounded collapsed" data-bs-toggle="collapse"
                            @click="collapseOpen" data-bs-target="#report-collapse" aria-expanded="false">
                            <div class="btntext">
                                <h5> <span><i class="bi bi-bar-chart-line"></i></span> Report</h5>
                                <div class="plus-button" :class="{open: open}">
                                    <div class="plus-icon"></div>
                                </div>
                            </div>
                        </button>
                        <div class="collapse" id="report-collapse" style="">
                            <ul class="btn-toggle-nav fw-normal pb-1 small text-light">
                                
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">Settings</a></li>
                                <li>
                                    <i class="bi bi-dot "></i>
                                    <a href="#">saasd</a></li>
                            </ul>
                        </div>
                    </li>
                </ul>
            </div>


        </div>
    </section>

</template>

<script>
export default {
    name: "SideBar",
    data() {
        return {
            open: false,
        }
    },
    methods: {
        collapseOpen: function (event) {
            console.log(event.target)
            if (event.target.querySelector(".plus-button") === null) {
                event.target.parentNode.parentNode.querySelector(".plus-button").classList.toggle('open')
            } else {
                event.target.querySelector(".plus-button").classList.toggle('open')
            }

        },
        activeToggle: function (event) {
            for (const li of event.target.parentNode.parentNode.querySelectorAll(".nav-link")) {
                li.classList.remove("active");
            }
            event.target.parentNode.classList.toggle('active')
        }
    }
}
</script>

<style>
:root {
    --bgcolor: #F5F7F8;
    --sidebarbg: #393D42;
    --collapsedbg: #32363A;
    --pillsidebarbg: #2A2F33;
    --sidebarred: #F55661;

}
header{
    height: 53px;
    background-color: rgba(49, 54, 59, 1);
    margin: 0;
    padding: 0;
}

.side {
    position: fixed;
}

.sidebar {
    display: flex;
    flex-wrap: nowrap;
    height: 100vh;
    overflow-x: auto;
    overflow-y: hidden;

}

.sideBarFirst {
    background-color: rgba(42, 47, 51, 1);
}

.sideBarSec {
    background-color: var(--sidebarbg);

}



.sideBarFirst .nav li {


    margin: auto;
    margin-top: 5px;
    margin-bottom: 10px;
    position: relative;
}




.sideBarFirst .nav-link img{
    opacity: .3;
}

.sideBarFirst .nav-link.active img{
    opacity: 1;
    background-color: unset;

}
.sideBarFirst .nav-link.active{
    
    background-color: unset;

}

.sideBarFirst .nav-link.active::before {
    content: "\00a0";
    position: absolute;
    background-color: #F55661;
    left: 0%;
    height: 70%;
    border-radius: 20%;

}

.bi {
    vertical-align: -.125em;
    pointer-events: none;
    fill: currentColor;
}

.dropdown-toggle {
    outline: 0;
}

.nav-flush .nav-link {
    border-radius: 0;
}

.btn-toggle {
    display: inline-flex;
    flex-direction: column;
    padding: .25rem .5rem;
    font-weight: 600;
    color: rgba(0, 0, 0, .65);
    background-color: transparent;
    border: 0;
    width: 100%;
    padding: 0 !important;
}



/* .btn-toggle::before {
    width: 1.25em;
    line-height: 0;
    content: url("data:image/svg+xml,%3csvg xmlns='http://www.w3.org/2000/svg' width='16' height='16' viewBox='0 0 16 16'%3e%3cpath fill='none' stroke='rgba%280,0,0,.5%29' stroke-linecap='round' stroke-linejoin='round' stroke-width='2' d='M5 14l6-6-6-6'/%3e%3c/svg%3e");
    transition: transform .35s ease;
    transform-origin: .5em 50%;
} */

.btn-toggle[aria-expanded="true"] {
    color: rgba(0, 0, 0, .85);
}

.btn-toggle[aria-expanded="true"]::before {
    transform: rotate(90deg);
}

.btn-toggle-nav a {

    text-decoration: none;
}

.btn-toggle-nav li {
    padding: 0.1875rem 0;
    margin-top: 0.125rem;
    margin-left: -.5rem;
    list-style: none;

}
.btn-toggle-nav li i{
    font-size: 25px;
}

.scrollarea {
    overflow-y: auto;
}

.fw-semibold {
    font-weight: 600;
}

.lh-tight {
    line-height: 1.25;
}


.btntext {
    position: relative;
    display: flex;
    width: 100%;


    height: 3rem;
}

.btn-toggle:not(.collapsed) .btntext {
    background-color: var(--sidebarred);
    transition: all .5s;
}

.plus-button {
    margin: auto 1rem auto auto;
    order: 2;
    cursor: pointer;
    transition: .3s;
}



.plus-icon {
    display: block;
    width: 20px;
    height: 3px;
    background-color: var(--bgcolor);
    opacity: .8;
    background-repeat: no-repeat;
    background-size: 1.5em 1.5em;
    user-select: none;
    border-radius: 0.75em;
    color: green;
    transition: .3s;
    position: relative;
}

.plus-icon:before {
    display: block;
    width: 20px;
    height: 3px;
    background-repeat: no-repeat;
    background-size: 3px 3px;
    user-select: none;
    border-radius: 0.75em;
    transition: .3s;
    position: absolute;
    content: '';
    transform-origin: 10px center;
    transform: rotate3d(0, 0, 1, 90deg);
    color: red;
    background-color: var(--bgcolor);
}

.open.plus-button .plus-icon:before,
.open.plus-button {
    top: 0;
    width: 20px;
    transform: rotate3d(0, 0, 0, 90deg);
}

.btn-toggle-nav li a{
    font-family: 'Raleway', sans-serif;
    color: #FFFFFF;
    opacity: .9;
}
.btn-toggle-nav li:hover a, .btn-toggle-nav li:hover{
    
    color: var(--sidebarred);
    
}

.btntext h5 {
    font-family: 'Raleway', sans-serif;
    margin: auto 0;
    text-transform: uppercase;
    font-size: .9rem;
    font-weight: 600;
    color: #FFFEFE;


}

.btntext h5 span {
    color: var(--sidebarred);
    margin: 1rem;
    font-size: 1.3rem;
}

.btn-toggle:not(.collapsed) .btntext h5 span {
    color: #FFFEFE;
}


.collapse.show {
    padding-top: 2rem;
    margin-top: -2rem;
    background-color: var(--collapsedbg);
    transition: all .5s;
}

.btn-toggle:not(.collapsed)::after {
    content: "";
    position: relative;
    top: 0;
    right: -1rem;
    width: 0;
    height: 0;
    border-style: solid;
    border-width: 10px 15px 0 15px;
    border-color: var(--sidebarred) transparent transparent transparent;
    animation: fadeInFromTop 1s ease-out forwards;

}

@keyframes fadeInFromTop {
    0% {
        opacity: 0;
        transform: translateY(-20px);
    }

    50% {
        opacity: 0;

    }

    100% {
        opacity: 1;
        transform: translateY(0);
    }
}
</style>
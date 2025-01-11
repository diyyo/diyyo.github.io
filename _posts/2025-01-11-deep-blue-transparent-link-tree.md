---
layout: post
title: Deep Blue Transparent Link Tree
date: 2025-01-11 19:14 +0700
categories: [Project]
tags: [code, sourcecode, linktree, html, css, javascript]
---

If you want to have a full custom Link Tree but do not understand coding, please copy the code below freely and for free. For a live preview of the finished project you can see [here][demo].

**Project Preview: [Live Demo][demo]**

## Import Font Awesome
Place the code below in the HTML header section `<head></head>`.
```html
<script src="https://kit.fontawesome.com/e588c08aea.js" crossorigin="anonymous"></script>
```

## Add CSS Stylesheet
Place the code below in the HTML style section `<style></style>`.
```css
    @import url('https://fonts.googleapis.com/css2?family=Oxanium:wght@200..800&display=swap');

    * {
        margin: 0;
        padding: 0;
        outline: none;
        list-style: none;
        text-decoration: none;
        box-sizing: border-box;
        background: transparent;
        border: none;
    }

    body {
        background: #10121C;
        font-family: "Oxanium", sans-serif;
        overflow: hidden;
        -webkit-user-drag: none;
        color: #fff;
        text-align: center;
    }

    html,
    body {
        margin: 0;
        padding: 0;
        height: 100%;
        width: 100%;
    }


    main {
        height: 100vh;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    #particleCanvas {
        width: 100%;
        height: 100%;
        position: fixed;
        top: 0;
        left: 0;
    }

    h1 {
        font-size: 2rem;
        font-weight: 200;
        color: #9dc3f7;
        position: relative;
        width: fit-content;
        margin-right: auto;
        margin-left: auto;
        margin-bottom: 16px;

        span {
            background: radial-gradient(2em 2em at 50% 50%, transparent calc(var(--p) - 2em), #fff calc(var(--p) - 1em), #fff calc(var(--p) - 0.4em), transparent var(--p)), linear-gradient(0deg, #bad1f1 30%, #9dc3f7 100%);
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            text-shadow: 0 2px 16px rgba(174, 207, 242, .24);
            --p: 0%;
        }

        span:first-of-type {
            user-select: none;
        }

        span:last-of-type {
            position: absolute;
            top: 0;
            left: 0;
            background: radial-gradient(2em 2em at 50% 50%, transparent calc(var(--p) - 2em), transparent calc(var(--p) - 1em), #fff calc(var(--p) - 1em), #fff calc(var(--p) - 0.4em), transparent calc(var(--p) - 0.4em), transparent var(--p));
            background-clip: text;
            -webkit-background-clip: text;
            -webkit-text-fill-color: transparent;
            filter: blur(16px) opacity(0.4);
        }

    }


    .card {
        max-width: 360px;
        width: 80%;
        padding: 48px;
        position: absolute;
        z-index: 10;
        top: 50%;
        left: 50%;
        text-align: center;
        transform: translate(-50%, -50%);
        padding: 32px 30px 16px;
        display: flex;
        align-items: center;
        -webkit-backdrop-filter: blur(2px);
        backdrop-filter: blur(2px);
        border-radius: 8px;
        box-shadow: 0 4px 90px rgba(0, 0, 0, 0.1);
        overflow: hidden;

        &:before {
            content: "";
            position: absolute;
            z-index: 2;
            top: 0;
            left: 0;
            width: 100%;
            height: 2px;
            background: rgb(255, 255, 255);
            background: linear-gradient(90deg, rgba(255, 255, 255, 0) 0%, rgba(255, 255, 255, 1) 34%, rgba(255, 255, 255, 1) 89%, rgba(255, 255, 255, 0) 100%);
            opacity: 0.3;
            filter: blur(.5px);
            mix-blend-mode: hard-light;
        }


        .noise {
            position: absolute;
            top: 0;
            left: 0;
            height: 100%;
            width: 100%;
            z-index: 1;
            opacity: 0.02;
        }

        .content {
            position: relative;
            z-index: 2;
            text-shadow: -3px 0px 2px rgba(0, 0, 0, 0.1);

            p {
                color: #9dc3f7;
                line-height: 140%;
                margin: 16px 0 24px;
                font-size: 14px;
            }
        }
    }

    a {
        text-transform: none;
        margin-bottom: 8px;
        border-radius: 10px;
        align-items: center;
        justify-content: center;
        text-decoration: none;
        padding: 15px 15px;
        position: relative;
        display: block;
        text-align: center;
        text-decoration: none;
        color: #9dc3f7;
        cursor: pointer;
        transition: all 0.3s ease;
        box-shadow: inset 2px 2px 2px 0px #9dc3f77e,
            7px 7px 20px 0px rgba(0, 0, 0, .1),
            4px 4px 5px 0px rgba(0, 0, 0, .1);
        outline: none;
        background: #ffffff25;
        background: linear-gradient(0deg, #ffffff25 0%, #ffffff25 100%);
    }

    a:hover {
        background: transparent;
    }

    a i {
        position: absolute;
        left: 15px;
    }

    a span {
        flex-grow: 1;
        text-align: center;
        font-size: 15px;
    }

    .avatar {
        border-radius: 50%;
        display: block;
        margin: 20px 0px 0px;
        width: 35%;
        margin-left: auto;
        margin-right: auto;
    }
```

## Add HTML Content
Place the code below in the HTML body section `<body></body>`.
```html
    <canvas id="particleCanvas"></canvas>
    <main>
        <div class="card">
            <svg viewBox="0 0 100% 100%" xmlns='http://www.w3.org/2000/svg' class="noise">
                <filter id='noiseFilter'>
                    <feTurbulence type='fractalNoise' baseFrequency='0.85' numOctaves='6' stitchTiles='stitch' />
                </filter>

                <rect width='100%' height='100%' preserveAspectRatio="xMidYMid meet" filter='url(#noiseFilter)' />
            </svg>
            <div class="content">
                <img draggable="false" contextmenu="return false;" class="avatar"
                    src="https://cdn-diyyo.web.app/src/icon/diyyoavatar.png" alt="diyyoavatar" />
                <h1 style="margin-top: 10px">
                    <span>diyyo White</span>
                    <span>diyyo White</span>
                </h1>
                <p>
                    Love does much, money does everything.
                </p>
                <a target="_blank" href="mailto:diyyowhite@gmail.com">
                    <i class="fa-solid fa-envelope"></i>
                    <span>Email</span>
                </a>
                <a target="_blank" href="https://x.com/diyyowhite">
                    <i class="fa-brands fa-x-twitter"></i>
                    <span>Twitter</span>
                </a>
                <a target="_blank" href="https://paravers.web.app">
                    <i class="fa-brands fa-discord"></i>
                    <span>Discord</span>
                </a>
                <a target="_blank" href="#">
                    <i class="fa-brands fa-instagram"></i>
                    <span>Instagram</span>
                </a>

            </div>
        </div>
    </main>
```

## Add Javascript
Place the code below in the HTML script section `<script></script>`.
```javascript
    const canvas = document.getElementById('particleCanvas');
    const ctx = canvas.getContext('2d');

    canvas.width = window.innerWidth;
    canvas.height = window.innerHeight;

    let particles = [];

    class Particle {
        constructor() {
            this.reset();
        }

        reset() {
            this.x = Math.random() * canvas.width;
            this.y = Math.random() * canvas.height;
            this.speed = Math.random() / 5 + 0.1;
            this.opacity = 1;
            this.fadeStart = Date.now() + Math.random() * 600 + 100;
            this.fadingOut = false;
        }

        update() {
            this.y -= this.speed;
            if (this.y < 0 || (this.fadingOut && (this.opacity -= 0.008) <= 0)) {
                this.reset();
            }
            if (!this.fadingOut && Date.now() > this.fadeStart) {
                this.fadingOut = true;
            }
        }

        draw() {
            ctx.fillStyle = `rgba(${255 - (Math.random() * 127.5)}, 255, 255, ${this.opacity})`;
            ctx.fillRect(this.x, this.y, 0.4, Math.random() * 2 + 1);
        }
    }

    function initParticles() {
        particles = Array.from({ length: Math.floor((canvas.width * canvas.height) / 6000) }, () => new Particle());
    }

    function animate() {
        ctx.clearRect(0, 0, canvas.width, canvas.height);
        particles.forEach(p => { p.update(); p.draw(); });
        requestAnimationFrame(animate);
    }

    window.addEventListener('resize', () => {
        canvas.width = window.innerWidth;
        canvas.height = window.innerHeight;
        initParticles();
    });

    initParticles();
    animate();
```

## Credits
Special thanks are given to each of the amazing people below.
> Some parts of this project are not made by diyyo, if you feel the author of some parts of this project please contact us or leave a comment below.
{: .prompt-info }

---

If you do not understand or have any other questions, please comment below, we will try to answer all your questions.

[demo]: https://diyyo.pages.dev
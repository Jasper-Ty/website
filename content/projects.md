+++
title = "Projects"

updated = 2023-12-20
+++

This is a very much non-exhaustive list of personal projects I've done.

(Click images for full size)

## jqoiview

<div>
    <a class="imglink" href="/img/jqoiview.png" target="_blank" width="100%">
        <img src="/img/jqoiview.png" width="100%">
    </a>
</div>

Program written in Rust for viewing the highly efficient [QOI](https://qoiformat.org) image format. Uses SDL2.

[Source](https://github.com/Jasper-Ty/jqoiview)
[crates.io](https://crates.io/crates/jqoiview)

## dither\_\{png,bmp\}

<div style="display: flex;">
    <a class="imglink" href="/img/santorini.png" target="_blank" width="50%">
        <img src="/img/santorini.png" width="100%">
    </a>
    <a class="imglink" href="/img/santorini_dithered.png" target="_blank" width="50%">
        <img src="/img/santorini_dithered.png" width="100%">
    </a>
</div>
<div>
    <a class="imglink" href="/img/your_name_dithered.bmp" target="_blank" width="100%">
        <img src="/img/your_name_dithered.bmp" width="100%">
    </a>
</div>

Command-line programs written in C (dither\_png) and Rust (dither\_bmp) that dither images.

[Source (dither\_png)](https://github.com/Jasper-Ty/dither_png)
[Source (dither\_bmp)](https://github.com/Jasper-Ty/dither_bmp)

## jtracer 

<div>
    <a class="imglink" href="/img/jtracer.png" target="_blank" width="100%">
        <img src="/img/jtracer.png" width="100%">
    </a>
</div>

My undergraduate computer graphics class covered ray tracing, but did not ask us to implement it. 

So here is my work-in-progress ray tracing example, written in Rust. 

[Source](https://github.com/Jasper-Ty/jtracer)

## j3sg

An unfinished static site generator and web server, written in Rust with actix\_web and Tera. Currently supports basic templating and hot-reloading.

A previous iteration of this site was built with j3sg. Currently, though, my site is built with [Zola](https://www.getzola.org/)

[Source](https://github.com/Jasper-Ty/j3sg)

## rustsweeper

<div>
    <a class="imglink" href="/img/rustsweeper.png" target="_blank" width="100%">
        <img src="/img/rustsweeper.png" width="100%">
    </a>
</div>

Work-in-progress clone of Minesweeper written in Rust. At the moment, it's using SDL2, but I may move it to [Bevy](https://bevyengine.org/). Someday I hope it reaches feature parity with [Minesweeper Arbiter]("https://minesweepergame.com/download/arbiter.php") (the current standard Minesweeper clone)

[Source](https://github.com/Jasper-Ty/rustsweeper)

## wordle solver

<div>
    <a class="imglink" href="/img/wordlesolver.png" target="_blank" width="100%">
        <img src="/img/wordlesolver.png" width="100%">
    </a>
</div>

Back when wordle was a craze, I quickly cooked up a solver for it in Python, basing it off of how Donald Knuth proved Mastermind can be solved in at most 5 moves using a maxmin algorithm. (Mastermind is one of my favorite puzzles).

It is hilariously slow due to the naiveness of both approach and implementation. I wrote an optimized version in C at some point, but the code for that is lost to time.

[Source (.py download link)](/static/misc/wordle_cmdline_solver.py)

# Astro v3 markdown page router Chinese unreadable characters bug minimal reproduction

## Bug description

In Astro v3, without using content collection and layout, only create markdown files under pages to use page routing, when `astro dev`, Chinese characters are unreadable. After `astro build`, the preview is correct.

## Steps to reproduce

- Create `test.md` file under pages, enter Chinese content
- Run `astro dev`
- View the page on `http://localhost:4321/test`，Chinese characters are unreadable

## Expected behavior

Chinese characters are readable

## astro version

windows 10

v3.0.0 - v3.1.4 are all have this bug

v2.10.15 was fine

`astro build` is fine

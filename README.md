# Next.js 15 App Router getStaticProps Issue

This repository demonstrates a seemingly simple issue encountered when using `getStaticProps` within Next.js 15's App Router without specifying the `revalidate` option.

## Problem Description

The `pages/index.js` file utilizes `getStaticProps`. When deployed, any changes to the data fetched by this function do not reflect on the client-side unless the browser cache is manually cleared. This issue seemingly contradicts the expected behavior of `getStaticProps` which should revalidate and regenerate the page content after a specific interval, as set by revalidate. This is particularly apparent when there's no `revalidate` option.

## Steps to reproduce

1. Clone this repository.
2. Run `npm install` to install dependencies.
3. Run `npm run dev` to start the development server.
4. Modify the `getStaticProps` function in `pages/index.js` to return different data.
5. Observe that the changes are not reflected in the browser without manually clearing the cache.

## Solution

The solution is simply to specify the `revalidate` option with any positive integer value in `getStaticProps`. This ensures that the page is regenerated at a specific interval.
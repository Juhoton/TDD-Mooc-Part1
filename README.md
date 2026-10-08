# [TDD MOOC Exercise 1](https://tdd.mooc.fi): Small, safe steps

Refactoring exercise about converting the usage of JS Date to Temporal.PlainDate. The main focus was to do the refactoring with incremental steps, meaning only changing 1-3 lines at a time, and getting the test pass. 

## First attempt, Parallel Changes (Branch 404)

The attempt took slightly over an hour. It took some time getting back to coding, and some reading about the Date and Temporal.PlainDate. The parallel changes refactoring method was easy to understand and use. Using temp names like date2 left convenient markers for changes, that made it easy to know what functions were refactored and what weren't. In the process of resetting the exercise for an another attempt, I accidentally removed the logs for the attempt, so there's no record of this attempt.

## Second Attempt, Conversion Propagation, TCR Max Changes 2 (Branch Refactor2)

This method took some time to understand, but was easy to use after that. I made a temp conversion function, that then made it possible to refactor the functions from the bottom up, each time pushing the conversion function call further up. 

The max changes 2 limit mostly made me do some weird steps with the code, like opening a function had to be done in steps. It also made it necessary to modify the temp conversion function to return the date value back if it was already converted to the Temporal.PlainDate. A better way to do it was probably to make it check if the given value was Date object, and either convert it if it was, or return it if it wasn't. I'm not sure if the limit making me realize the need for that and making me do the modification was a good thing --- especially when talking about a temp function --- but I probably wouldn't have done it if it wasn't there. 

The TCR was an interesting way to code, but I feel like it just made me rewrite the same lines more often than actually help. I do like the autotesting feature, where with every change I can just quickly check if anything breaks. The forced revert however just feel like it breaks the workflow more than help. It does force you to do incremental steps, but if you can have the discipline to do it on your own, the reverting just feels unnecessary. 

## Third Attempt, Parallel Changes, TCR Max Changes 1 (Branch Main)

This was more of a challenge than a real method to follow. The parallel function for the new parseDate method had to be written in a single line, which feels illegal. The challenge does force you to think in different ways than normal, so there's some benefit. It also forces you to write one liners, so it's a good way to learn about those. 



---

_This exercise is part of the [TDD MOOC](https://tdd.mooc.fi) at the University of Helsinki, brought to you
by [Esko Luontola](https://twitter.com/EskoLuontola) and [Nitor](https://nitor.com/). This exercise is based on
the [Lift Pass Pricing Refactoring Kata](https://github.com/martinsson/Refactoring-Kata-Lift-Pass-Pricing)
by [Johan Martinsson](https://twitter.com/johan_alps)._

## Prerequisites

You'll need a recent [Node.js](https://nodejs.org/) version. Then download this project's dependencies with:

    npm install

## Developing

This project uses [Vitest](https://vitest.dev/), [Chai](https://www.chaijs.com/)
and [SuperTest](https://github.com/visionmedia/supertest) for testing.

Run tests once

    npm run test

Run tests continuously

    npm run autotest

Run tests [TCR](https://medium.com/@kentbeck_7670/test-commit-revert-870bbd756864) style. Defaults to `MAX_CHANGES=1`

    npm run tcr
    MAX_CHANGES=2 npm run tcr

Start the application

    npm run start

Code reformat

    npm run format

---
layout: post
title:  Retirement Savings Calculator v 2.4 is live!
date: 2023-03-20 18:15:00+8
description: Hello!
tags: financial spreadsheets
categories: 
---

The Retirement Savings Calculator Spreadsheet is a tool designed to help individuals calculate how much they can save and accumulate based on different levels of savings and expenditures. As of 20 March 2023, the latest version of the tool is v2.4, and is publicly available [here](https://docs.google.com/spreadsheets/d/1wKXRlBWTYL16pFi9IdsrThDQC5q2jKmeqlKNkPufefI). 

Do make your own copy for yourself via "File" > "Make a copy".

Do share your feedback on the calculator via the [feedback form](https://docs.google.com/forms/d/e/1FAIpQLScswYDxLhregN4xUfROgkLVpPJItCGwtvXNHUHqep_RTe5lrw/viewform?usp=sharing).

## Stuff
- summary intro
- history
- context
- features
- what it doesn't do
- alternatives


## Contents
* This will become a table of contents (this text will be scrapped).
{:toc}

## Overview
I've created a [Retirement Savings calculator](https://docs.google.com/spreadsheets/d/1wKXRlBWTYL16pFi9IdsrThDQC5q2jKmeqlKNkPufefI) in Google Sheets that I use to help me plan out how to save for retirement. This post will be talking more about my rationale and thoughts behind the creation of the calculator, and not so much of a guide to using the calculator. If you are looking for a usage guide, [this](https://www.gerardchan.com/projects/savings_calculator) is the page you seek.

## How it started
When I first started working, I was faced with the decision of how much of my income should I save in order to have enough for retirement. Understandably, that question can't be answered without asking other questions like "When do I plan to retire?" or "How much do I need to retire?". 

This evolved into creating an ad hoc spreadsheet to key in dates from now till the year I wanted to retire, my projected income, pre- and post-retirement expenses, and projecting the amount of savings I would have over time. I got an answer, and more questions came to mind. What if inflation is higher?  What if I cut my expenses by this much? What if I retired this much later? There were so many formulas to tweak, so many values to change, and it was so much work to answer the questions I was asking.

This led me to think more clearly about 
- what key variables I wanted to vary each iteration during planning
- what were the key outputs I was interested in 
- what calculations needed to be done, but didn't require me to review the outputs every single time input variables changed

The result was the first Retirement Savings Calculator. Over the years, I've added more features, such as CPF Life, income tax calculations, cash buffer, and couple planning. I'm not at the point where I feel "I've solved my retirement plan!", but I've got a better understanding of the steps I need to take to hit achieve my retirement goals.

## Context
- Singapore
- CPF Life
- sg income tax
- no capital gains
- likely only one major purchase with loan (house)
- no complex variables like kids or saving up for a house

The Retirement Savings Calculator is tailored to handle a fairly simple context, as far as financial planning goes. Below are some aspects of that context, and their implications.

### Singapore Personal Income Tax Brackets
The calculator only computes tax amounts based on Singapore Personal Income Tax Brackets. Singapore has one of the most straightforward progressive tax rules, and so this was something that I felt confident I could write spreadsheet formulas to handle.

### Singapore has no Capital Gains Tax
As Singapore has no Capital Gains Tax, selling from one's portfolio yields the full value as cash without any complex tax overheads.

### CPF Life
CPF is Singapore's mandatory savings and pension plan, with CPF Life as its related annuity. The impact that it has on retirement planning is significant, and I couldn't omit it without throwing my numbers way off.

### No customisable big purchases
The spreadsheet doesn't allow for a way to enter custom big purchases or spends at or over various periods of time. For example, some people might set aside a certain amount of money for the next 5 years to save up for a wedding, or a car, or a house, after which that expense ceases. Implementing the calculations as well as a user friendly input mechanism for this in a spreadsheet is something I haven't solved, yet. At this level of complexity, I think a web application with a proper front-end and database would be more suitable than a spreadsheet.

## How the spreadsheet works
### Before Retirement
- Savings are accumulated in a portfolio, with allocation percetanges and yield set by the user
- Savings amounts each year are calculated based on the chosen strategy (Free Cash vs Savings Committment)
- CPF is accumulated based on salary

### After Retirement
- 3 years of savings are withdrawn and held as cash. This provides a cash buffer to draw from during market downturns to reduce the need to sell stocks and bonds at a loss
- Each year, the inflation-adjusted amount needed to support retirement expenses is withdrawn from the portfolio
- Once a person reaches the age where CPF Life can start paying out (currently 65 as of 2023), they receive CPF Life payouts, and portfolio withdrawals are reduced by this amount
- Retirees draw from their portfolio until their end of life

## Features
One of the major motivations for guiding what features to implement and how to implement them was my desire to be able to specify my plan in a few paramaters, rather than having to do a year-by-year play for items like savings and expenditure. This has resulted in a design where you can key the input parameters fairly succinctly on the input page, and then receive the graphical outputs to assess the outcome of your parameters.

### Savings Strategy: Savings committments
The Savings Commitments feature is one of two savings strategies available for users to select from. With this feature, users can set a monthly or annual savings goal and increment it by a flat amount or percentage each year. This strategy is suited to users who want to prioritise their savings first, and then spend what's left over.

This was the original savings strategy in the first version of the spreadsheet. The question of "If I saved this much each month, is that enough for me retire?" was what spurred me to create the Retirement Savings Calculator, and this savings strategy was the first one I wanted to asses as part of my possible plan.

### Savings Strategy: Free Cash
When my salary started increasing, I wanted to increase my savings rate while keeping my expenses constant aside from inflation adjustments. The Savings Commitments strategy didn't quite enable me to capture this succinctly. From this need, the Free Cash strategy was designed. It enabled me to set my expenses and adjust them based on inflation, and set my salary and increment it annually based on what I felt I would be able to attain as an average increment.

### CPF Life
CPF Life provides an extremely cost efficient means of securing a guaranteed lifelong income. From my comparisons to other commercially available annuities, it simply offers a much higher guaranteed return, with the limitation of your premium being subject to a cap. The cap will allow you to have a reasonable income to survive on and be self sufficient, but not support more luxurious spending. If you are looking to have at least a middle class income in retirement, you will still need additional sources of income in retirement.

If you have access to CPF Life, it will likely form an excellent base for your retirement income, upon which you can build upon towards your target retirement income level.

For the spreadsheet calculator, I have chosen to have CPF Life start paying out on the Standard Plan at the earliest possible age. Based on my calculations, the Escalating plan and the increased monthly payout from the deferred payout start date simply took too long to break even. For simplicity's sake, I decided to focus on implementing the plan that would be the most supportive of generating income to support retirement.

- Withdrawal rate and rationale
- Portfolio amount (and the shortcoming of just looking at the amount. Going upwards slower than inflation still means increasing withdrawal rate)

## what it doesn't do
- Doesn't handle capital gains taxes (sg no have)
- Doesn't handle different country taxes (complex systems of deductions and rates)
- Handle Complex dynamic costs over time (kids, college, caring for elderly). Limitations on dynamic-ness of sheets data structure, and ease of interface to enter them
- tell you what portfolio allocation is best
- tell you what rate of return the market will give
- tell you what stocks to buy
- help you estimate your income or expenses
- this is meant to be a starting point to help consider some of the factors needed in retirement planning, and highlight the compounding effects of time

## Follow ups for you
- Thigns to consider
    - list down your dependents
    - take stock of your liabilities (loans, upcoming college fees for kids, ongoing medical)
    - talk about for your potential retirement costs (eg long term care when you become less able)
    - Explore money management towards and during retirement
        - sequence of return risk mitigation (eg withdrawal rates, glidepaths)
        - annuities
        - bucket strategy (link)
- Talk to your financial planner
- Consider trying UP (link)

## What do you want next?
- what kinds of things you wanna hear more about next?

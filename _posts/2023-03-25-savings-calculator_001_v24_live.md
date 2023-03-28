---
layout: post
title:  Retirement Savings Calculator v 2.4 is live!
date: 2024-03-20 18:15:00+8
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
I've created a [Retirement Savings calculator](https://docs.google.com/spreadsheets/d/1wKXRlBWTYL16pFi9IdsrThDQC5q2jKmeqlKNkPufefI) in Google Sheets that I use to help me plan out how to save for retirement. This 

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
The spreadsheet doesn't allow for a way to enter custom big purchases or spends at or over various periods of time. For example, some people might set aside a certain amount of money for the next 5 years to save up for a wedding, or a car, or a house, after which that expense ceases. Implementing the calculations as well as a user friendly input mechanism for this in a spreadsheet is something I haven't solved, yet. At this level of complexity, I do question if a spreadsheet is even the right medium for this.

## How the spreadsheet works
### Before Retirement
- Savings are accumulated in a portfolio, with allocation percetanges and yield set by the user
- Savings amounts each year are calculated based on the chosen strategy (Free Cash vs Savings Committment)
- CPF is accumulated based on salary

### After Retirement
- 3 years of savings are withdrwan and held as cash. This helps buffer against any sudden market downturns
- Each year, the inflation-adjusted amount needed to support retirement expenses is withdrawn from the portfolio
- Once a person reaches the age where CPF Life can start paying out (currently 65 as of 2023), they receive CPF Life payouts, and portfolio withdrawals are reduced by this amount
- Retirees draw from their portfolio until their end of life

## Features
- Savings committments strategy
- Free cash strategy (evolution from savings committment)
    - Didn't want to increase expenses more than inflation, and wanted savings rate to increase with increasing salary
- CPF Life (with sum selection and top ups)
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

---
layout: post
title:  Retirement Savings Calculator v 2.4 is live!
date: 2023-03-29 17:03:00+8
description: How the Savings Calculator came to be, and some key features
tags: financial spreadsheets
categories: 
---

The Retirement Savings Calculator Spreadsheet is a tool designed to help individuals calculate how much they can save and accumulate based on different levels of savings and expenditures. As of 29 March 2023, the latest version of the tool is v2.4, and is publicly available [here](https://docs.google.com/spreadsheets/d/1wKXRlBWTYL16pFi9IdsrThDQC5q2jKmeqlKNkPufefI). 

Do make your own copy for yourself via "File" > "Make a copy".

Do share your feedback on the calculator via the [feedback form](https://docs.google.com/forms/d/e/1FAIpQLScswYDxLhregN4xUfROgkLVpPJItCGwtvXNHUHqep_RTe5lrw/viewform?usp=sharing).


## Contents
* This will become a table of contents (this text will be scrapped).
{:toc}

## Overview
I've created a [Retirement Savings calculator](https://docs.google.com/spreadsheets/d/1wKXRlBWTYL16pFi9IdsrThDQC5q2jKmeqlKNkPufefI) in Google Sheets that I use to help me plan out how to save for retirement. This post will be talking more about my rationale and thoughts behind the creation of the calculator, and not so much of a guide to using the calculator. If you are looking for a usage guide, [this](https://www.gerardchan.com/projects/savings_calculator) is the page you seek.

{% include figure.html path="assets/img/savings_calc/savings_calc_plan.png" class="img-fluid rounded z-depth-1" zoomable=true %}

## How it started
When I first started working, I was faced with the decision of how much of my income should I save in order to have enough for retirement. Understandably, that question can't be answered without asking other questions like "When do I plan to retire?" or "How much do I need to retire?". 

This evolved into creating an ad hoc spreadsheet to key in dates from now till the year I wanted to retire, my projected income, pre- and post-retirement expenses, and projecting the amount of savings I would have over time. I got an answer, and more questions came to mind. What if inflation is higher?  What if I cut my expenses by this much? What if I retired this much later? There were so many formulas to tweak, so many values to change, and it was so much work to answer the questions I was asking.

This led me to think more clearly about 
- what key variables I wanted to vary each iteration during planning
- what were the key outputs I was interested in 
- what calculations needed to be done, but didn't require me to review the outputs every single time input variables changed

The result was the first Retirement Savings Calculator. Over the years, I've added more features, such as CPF Life, income tax calculations, cash buffer, and couple planning. I'm not at the point where I feel "I've solved my retirement plan!", but I've got a better understanding of the steps I need to take to hit achieve my retirement goals.

## Context
The Retirement Savings Calculator is tailored to handle a fairly simple context, as far as financial planning goes. Below are some aspects of that context, and their implications.

### Singapore Personal Income Tax Brackets
The calculator only computes tax amounts based on Singapore Personal Income Tax Brackets. Singapore has one of the most straightforward progressive tax rules, and so this was something that I felt confident I could write spreadsheet formulas to handle.

### Singapore has no Capital Gains Tax
As Singapore has no Capital Gains Tax, selling from one's portfolio yields the full value as cash without any complex tax overheads.

### CPF Life
CPF is Singapore's mandatory savings and pension plan, with CPF Life as its related annuity. The impact that it has on retirement planning is significant, and I couldn't omit it without throwing my numbers way off.

### No customisable big purchases
The spreadsheet doesn't allow for a way to enter custom big purchases or spends at or over various periods of time. For example, some people might set aside a certain amount of money for the next 5 years to save up for a wedding, or a car, or a house downpayment, after which that expense ceases. How to implement the calculations as well as a user friendly input mechanism for this in a spreadsheet is a challenge I haven't solved, yet. At this level of complexity, I think a web application with a proper front-end and database would be more suitable than a spreadsheet.

## How the spreadsheet works
### Before Retirement
- Savings are accumulated in a portfolio, with allocation percetanges and yield set by the user.
- Savings amounts each year are calculated based on the chosen strategy (Free Cash vs Savings Committment).
- CPF is accumulated based on salary.

### After Retirement
- 3 years of savings are withdrawn and held as cash. This provides a cash buffer to draw from during market downturns to reduce the need to sell stocks and bonds at a loss.
- Each year, the inflation-adjusted amount needed to support retirement expenses is withdrawn from the portfolio.
- Once a person reaches the age where CPF Life can start paying out (currently 65 as of 2023), they receive CPF Life payouts, and portfolio withdrawals are reduced by this amount
- Retirees draw from their portfolio until their end of life.

## Features
One of the major motivations for guiding what features to implement and how to implement them was my desire to be able to specify my plan in a few paramaters, rather than having to do a year-by-year play for items like savings and expenditure. This has resulted in a design where you can key the input parameters fairly succinctly on the input page, and then receive the graphical outputs to assess the outcome of your parameters.

### Savings Strategy: Savings committments
The Savings Commitments strategy is one of two savings strategies available for users to select from. With this feature, users can set a monthly or annual savings goal and increment it by a flat amount or percentage each year. This strategy is suited to users who want to prioritise their savings first, and then spend what's left over.

This was the original savings strategy in the first version of the spreadsheet. The question of "If I saved this much each month, is that enough for me retire?" was what spurred me to create the Retirement Savings Calculator, and this savings strategy was the first one I wanted to asses as part of my possible plan.

### Savings Strategy: Free Cash
When my salary started increasing, I wanted to increase my savings rate while keeping my expenses constant aside from inflation adjustments. The Savings Commitments strategy didn't quite enable me to capture this succinctly. From this need, the Free Cash strategy was designed. It enabled me to set my expenses and adjust them based on inflation, and set my salary and increment it annually based on what I felt I would be able to attain as an average increment.

### CPF Life
CPF Life provides an extremely cost efficient means of securing a guaranteed lifelong income. From my comparisons to other commercially available annuities, it simply offers a much higher guaranteed return, with the limitation of your premium being subject to a cap. The cap will allow you to have a reasonable income to survive on and be self sufficient, but not support more luxurious spending. If you are looking to have at least a middle class income in retirement, you will still need additional sources of income in retirement.

If you have access to CPF Life, it will likely form an excellent base for your retirement income, upon which you can build upon towards your target retirement income level.

For the spreadsheet calculator, I have chosen to have CPF Life start paying out on the Standard Plan at the earliest possible age. Based on my calculations, the Escalating plan and the increased monthly payout from the deferred payout start date simply took too long to break even, usually in your late 80s. For simplicity's sake, I decided to focus on implementing the plan that would be the most supportive of generating income to support retirement: Standard Plan with no deferred payout start.

### Chart: Savings Value

{% include figure.html path="assets/img/savings_calc/savings_calc_savings_value.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This is the chart that I initially built to monitor the value of the portfolio over time, both before and after retirement. If the upward growth of the chart slows or reverses, it signals that portfolio growth is not keeping up with inflation-adjusted retirement spending. The chart also gives a sense of the magnitude of the problem, and how soon it occurs. Does the current plan start running out of money in the last few years of life? Or does it run out of money just after retirement?

I did find the chart useful for detecting major issues in my retirement plan, but I did find that it was challenging to notice the slowdown in growth, especially later in retirement when absolute numbers are much larger. How would I be able to detect such signs earlier? This would be important in hedging against the risk of living longer than the planned age.

### Chart: Withdrawal Rate

{% include figure.html path="assets/img/savings_calc/savings_calc_withdrawal_rate.png" class="img-fluid rounded z-depth-1" zoomable=true %}

In order to better detect signs of the portfolio not being able to keep up with inflation adjusted retirement savings, the withdrawal rate chart was created. The withdrawal rate indicates what percentage of the portfolio is withdrwan in a given year. A 4% withdrawal rate in a given year means 4% of the portfolio was withdrawn that year. A rising withdrawal rate would indicate the portfolio losing ground against inflation adjusted retirement spending, as well as by how much.

From my experimentation, I've found that withdrawal rates above 5% are usually unsustainable unless one is more optimistic about future market returns than I am. Based on my own preferences, I intend to save up enough for retirement such that my withdrawal rate doesn't need to increase over time to support my retirement spending. This also gives me a comfortable amount of buffer room when (not if but when) there is a market downturn during retirement.

## What the Retirement Savings Calculator does not do
- **Compute Capital Gains Taxes**: Singapore doesn't have this (as of 2023).
- **Compute income tax values for countries other than Singapore**: Those are far more complex, and not within my current use case.
- **Handle dynamic costs over time (kids, college, caring for elderly)**: I haven't found a way to implement these in spreadsheets in a way that is not too onerous or complex for users to understand and key in inputs.
- **Tell you what portfolio allocation is best**: This is a whole topic in and of itself, and not in the scope of the spreadsheet.
- **Tell you what rate of return the market will give at any point in time**: If there's a spreadsheet that can do this, this isn't that spreadsheet.
- **Tell you what stocks/bonds/property/commodities to buy**: Like portfolio allocation, that's a whole topic beyond the scope of the spreadsheet
- **Help you estimate your income or expenses**: That's beyond the scope of this spreadsheet. For estimating expenses, I have used some methods to estimate and manage my expenses. Let me know in the [feedback form](https://docs.google.com/forms/d/e/1FAIpQLScswYDxLhregN4xUfROgkLVpPJItCGwtvXNHUHqep_RTe5lrw/viewform?usp=sharing) if this is something you'd like to see discussed in a future post!

## What Next?
After tinkering with the spreadsheet and getting a sense of how much you need to save to support a certain amount of retirement spending, it's time to refine those estimates. There's much more to consider in a retirement plan than how much you want to save and when you want to retire.

- Other parts of a financial plan to consider
    - List down your dependents, and how much you will need to support them over time.
    - Take stock of your liabilities (car/house/student loans, upcoming college fees for kids, ongoing medical costs).
    - Consider your potential retirement costs. Below are some examples.
        - Long term care when you become less able
        - Cost of moving to your retirement country of choice
        - Moving house to be nearer to your children
        - Rising healthcare costs in old age
    - Explore money management considerations towards and during retirement
        - How do you mitigate the risk of a market downturn shrinking your savings at the start of retirement, forcing a larger percentage withdrawal that then jeopardises your retirement (aka sequence of return risk)?
        - What instruments will you use to generate your retirement income? Annuities? Dividends? Selling stocks and bonds? All of the above?
        - Will you choose to use a cash buffer like I did here? Will you use a three year buffer or a larger or smaller buffer?
- Talk to your financial planner
- Consider trying [UP](https://www.upplan.sg/)
    - They've built a web application with many more features than I have in my spreadsheet.
    - It's much more feature rich than my spreadsheet, and can handle many more events such as house and car loans, and various one-time and continuous expenses AND incomes.
    - There is a really good tutorial-like wizard that helps guide you through the process in a step by step fashion. It's really very helpful.
    - UP has the capability to let you know when you run out of cash, or have too much savings, and advise you accordingly.
    - Disclosure: I have worked with the company behind UP in the past, but have no financial interest or any other relationship with them at this time.

## Thank you!
Thanks for reading! I hope you found it helpful and enjoyable.

What would you like to hear more about next? Do let me know in the feedback form!

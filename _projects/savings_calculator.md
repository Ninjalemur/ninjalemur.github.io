---
layout: page
title: Retirement Savings Calculator
description: A Calculator for Retirement Savings in Google Sheets
img: assets/img/temperate_forest_scenic.jpg
---

The Savings Calculator Spreadsheet is a tool designed to help individuals calculate how much they can save and accumulate based on different levels of savings and expenditures. As of 20 March 2023, the latest version of the tool is v2.4, and is available to the public via <a href="https://docs.google.com/spreadsheets/d/1wKXRlBWTYL16pFi9IdsrThDQC5q2jKmeqlKNkPufefI"> this link</a>. 

Do make your own copy for yourself via "File" > "Make a copy".

Do share your feedback on the calculator via the feedback form <a href="https://docs.google.com/forms/d/12nZ9wkob9Tmg9HqVHN-IEpG_HUIq2gxCxDd6VJo1aI8!">feedback form</a>.

## Contents
* This will become a table of contents (this text will be scrapped).
{:toc}

## Purpose

The purpose of this spreadsheet is to provide a basic calculation of how much one can accumulate and consume at various levels of savings and expenditure. The tool is useful for individuals who are planning to save money for retirement and want to estimate how much savings they will need to support spending in retirement.

[Back to Top](#Contents)

## Why Google Sheets?

The Savings Calculator Spreadsheet was created using Google Sheets as the tool of choice. One maing reason was that it would be free for me to develop, free for me to distribute, and free for users to use. Additionally, using Google Sheets ensures that the user's data is kept under their control, without giving me access to any of it. This is an essential feature as people would be keying in their own financial information to do their planning.

As a security choice, I have also chosen not to use any scripts in the calculator. I wouldn't feel safe enabling scripts on a spreadsheet from some guy on the internet before keying in financial data, and neither should you.

[Back to Top](#Contents)

## Getting your copy of the Savings Calculator

Once you have opened my public copy of the Savings Calculator, go to "File" > "Make a copy" to make a copy for yourself. The public copy is not editable, so that users cannot see each others inputs.
 
{% include figure.html path="assets/img/savings_calc/savings_calc_make_copy.png" class="img-fluid rounded z-depth-1" zoomable=true %}

Select a folder to save your own copy in, and press "Make a copy"

{% include figure.html path="assets/img/savings_calc/savings_calc_make_copy_save.png" class="img-fluid rounded z-depth-1" zoomable=true %}

## How does it work?
The Savings Calculator calculates the portfolio/savings value of the person or couple over time. This is based on the following sequence of events
1. Savings starts from the year **Start Saving in Year**
1. Each year before retirement, the portfolio grows based on returns as well as contributions to savings.
1. After retirement, contributions stop, and withdrawals commence.
1. If CPF is enabled, CPF Life Payouts will start at the CPF LIFE payout age. This will reduce the amount that is withdrawn from the portfolio to support retirement
1. At each person's death age, they will stop withdrawing their share of expenses.

Note that three years of retirement expenses (adjusted for inflation) are held as cash. In case of an economic downturn, this pool of cash aims to reduce the need to sell assets from your portfolio during a downturn.

## The Plan tab
The Plan tab is where the action happens. You can key in your desired parameters, and the Savings Calculator will estimate how your savings will look like over time, as visualised by the charts on the right.

{% include figure.html path="assets/img/savings_calc/savings_calc_plan.png" class="img-fluid rounded z-depth-1" zoomable=true %}

## Keying in your parameters

The savings calculator does require a number of parameters to help estimate your savings over time. The blue boxes in the spreadsheet will guide you what inputs to key in at each step. 

{% include figure.html path="assets/img/savings_calc/savings_calc_params_overview.png" class="img-fluid rounded z-depth-1" zoomable=true %}

Some parameters do have fields for two people. If you are planning solo, you can leave the second field blank or at zero.

## Parameters

### Dates and Targets
- **Today's Year:** Today's Year tells the calculator what year it is currently, so that it can correctly apply inflation to future years to compute your needed expenditures
- **Start Saving in Year:** Some people might be planning their savings in advance. You can key in a year equal to or later than Today's Year into this field to reflect that. This will tell the calculator what year your savings plan will commence.

### Assumptions about economy
- **High Yield Average Return:** Most people's portfolio contain High Yield assets (eg Stocks, Equity ETFs). Key in the average annual return you expect from such assets in percentage points.
- **Low Risk Average Return:** Most people's portfolio contain Low Risk assets (eg Bonds, T-Bills). Key in the average annual return you expect from such assets in percentage points.
- **Average Inflation:** The cost of stuff goes up over time. Key in how many percent points the stuff you buy is expected to go up each year.

### Your Portfolio
- **High Yield Allocation Percentage:** Key in what percentage of your portfolio is in High Yield assets (eg Stocks, Equity ETFs). The remaining percentage of your portfolio is assumed to be in Low Risk assets, and automatically computed.

### CPF Settings
- **CPF Retirement sum inflation:** This toggles whether the calculator will assume that CPF Retirement sums will continue to increase at a similar rate as they have in the past. Historically, CPF retirement sums have increase about 2.5-3.5% per year.

### Savings strategy
- **Strategy:** This selects which Savings Strategy the calculator will compute your future savings on
    - **Savings Committment:** In this strategy, you will save a target amount of savings every year or month, and increase that every year by a certain percentage or flat amount.
    - **Free Cash:** Instead of fixed targets, you will save whatever is left over from your gross salary after deducting the following
        - income tax
        - employee CPF contributions
        - expenses

If you prefer to plan your finances around "I will save this amount from my salary every year, and spend the rest", go for the Savings Committment. If you plan via "I will spend this much of my income and save the rest", go for Free Cash.

### Current Savings
- **Starting Savings:** Key in the dollar value of the savings that you currently have

### Free Cash Strategy
If you selected **Free Cash** as your Savings Strategy earlier, here is where you would key in the parameters for the strategy.
- **Current Annual Expenses:** This represents how much your expenses are each year in today's dollars. It will be adjusted for inflation to estimate how much your expenses will be from now until retirement
- **Starting Gross Basic Annual Salary:** This represents how much your gross annual salary is, before deductions like income tax and employee CPF contributions.
- **Annual increment:** Key in how much you expect your annual salary to increase by each year, either in percentage points, or dollar amounts.

### Savings Committments
If you selected **Savings Committments** as your Savings Strategy earlier, here is where you would key in the parameters for the strategy.
- **Annual Amount / Monthly Amount:** Select whether you would like to specify your savings committments monthly or annually, and key in that number. Whichever you select, the other will be computed and displayed for you in the following row
- **Annual Increment:** Select whether you would like to key in your annual increment in percentage or dollar amounts, and key in that number

### Desired Retirement Income (Today's dollars)
- **Annual Amount / Monthly Amount:** Select whether you would like to specify your retirement income monthly or annually, and key in that number. Whichever you select, the other will be computed and displayed for you in the following row. You don't need to key in an increment number here. That will be computed based on the inflation number you entered earlier.

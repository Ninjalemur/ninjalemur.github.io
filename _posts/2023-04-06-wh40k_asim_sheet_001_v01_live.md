---
layout: post
title:  Warhammer 40k 9th Edition Attack Simulator Spreadsheet v 0.1 is live!
date: 2023-03-29 17:03:00+8
description: Key Features and design choices of the 40k attack simulator spreadsheet
tags: financial spreadsheets
categories: 
---

## Contents
* This will become a table of contents (this text will be scrapped).
{:toc}

## Overview
- overview
- 10th ed is coming, but can change

## My history with 40k
- played with bro back in second edition
- always found strategic depth fascinating multitude of races and strategic choices within each race
- but found the time committment (painting and playing) and cost (rulebooks and models) prohibitive
- recently discovered tabletop simulator and wahapedia

## Motivation to create
- inspiration from original
- improvements
    - ease of maintenance
    - ease of replicating calculations
    - modularity between calculations and user input and charts
    - have more comparison use cases to reduce the need to switch inputs to visualise

## Design considerations
- Core calculation tabs (dmg_calc and morale_calc) that accept inputs and provide outputs
- User interface tabs that users interact with
- ref data tabs (alr in original)
- Helper tabs MP and Index
- Index provides list of lookups for data validation or VLOOKUP or string variable values
- MP provides lookup ranges for data columns using INDIRECT
- Data columns are named ranges to make code more readable
- formulas are indented to make them more readable

## What's next?
- want to create a more comprehensive analysis so that users can find the best combis via filter rather than manual input
- python based calculations, visualised in tableau public
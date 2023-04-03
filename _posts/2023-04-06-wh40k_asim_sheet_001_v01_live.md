---
layout: post
title:  Warhammer 40k 9th Edition Attack Simulator Spreadsheet v 0.1 is live!
date: 2023-04-6 08:33:00+8
description: Key Features and design choices of the 40k attack simulator spreadsheet
tags: financial spreadsheets
categories: 
---

## Contents
* This will become a table of contents (this text will be scrapped).
{:toc}

## Overview
The first version of my Warhammer 40k Attack simulator spreadsheet is available. It allows users to compute the points efficiency of attackers against defenders in the tabletop game Warhammer 40,000. Do make a copy from [here](https://www.gerardchan.com/projects/wh40k_9ed_attack_sim_sheet/), and feel free to share your thoughts in the feedback form! The new 10th edition of the game will launch in the coming months, and I look forward to updating the spreadsheet to accommodate the new set of rules then!

## What is Warhammer 40k?
Warhammer 40k is a tabletop miniatures wargame published by [Games Workshop](https://www.games-workshop.com/). Players battle on a tabletop using their own armies of painted miniatures. Distances for movement and weapon ranges are physically measured using a measuring tape, and combat is resolved via dice in a process known as the attack sequence. Unlike Risk, units are not all made equal. Different units have different statistics, strengths, and weaknesses which influence their chances of success when the dice are rolled.

I've always found the strategic depth of Warhammer 40k fascinating. Players can choose from a variety of factions to build their armies with. Each faction has a whole roster of different units to select from, and each unit can often be further customised with different wargear and weapon selections. Before the start of the battle, players have to choose where on the battlefield they wish to deploy their units, or even hold them in reserve for deployment midway through the battle. During the battle, where units are moved and what enemies they choose to attack is a huge determining factor in how much value they will deliver during the battle.

For the longest time, I hadn't really gotten into Warhammer 40k due to some barriers to entry. The time committment required was huge, with models needing to be painted before play, and games running on average between 3 to 4 hours. Cost was also not trivial, with an army of models usually costing a few hundred dollars (or more if you wanted to change up your roster now and then), and rulebooks usually costing $50 per faction.

Recently, I discovered [Tabletop Simulator](https://www.tabletopsimulator.com/), a PC game which can simulate a variety of games from chess, to mahjong, and with the help of some [Steam Workshop Mods](https://steamcommunity.com/sharedfiles/filedetails/?id=775431044), Warhammer 40k. This brings the cost of entry down significantly, saves me the trouble of painting, storing, and transporting miniatures, and provides some of the quality of life that the electronic medium can provide, such as electronically spawning large numbers of dice and tallying up the rolls automatically. I'm definitely looking forward to playing the game in this medium.

## Objective of creating my spreadsheet
The inspiration for my spreadsheet was from a version shared by figrin1 on [Reddit](https://www.reddit.com/r/WarhammerCompetitive/comments/i6ubf9/ultracomprehensive_and_pretty_updated_mathhammer/). It provides a user interface and calculations to answer the question of "If this attacker attacks this defender, how many points of damage did the attacker deal relative to its own points cost?" The spreadsheet allows a user to select an attacker, up to three weapons for the attacker, and a defender.

 After using his spreadsheet for a while, I was inspired to build my own to improve on the original in two key areas
1. Increase ease of maintenance and expandability
1. Lower the effort needed to create new use cases

In order to achieve those goals, I implemented a number of design choices
1. Separate the front-end user interface from the back-end calculations
1. Use ARRAYFORMULA for calculations
1. Consolidate Keywords (eg "Rapid Fire") in a single tab
1. Use Named Ranges for column names
1. Use [BattleScribe data](https://github.com/BSData/wh40k) as a data source

### Goal: Increase ease of maintenance
Attack Math in Warhammer 40k takes in a large number of inputs, ranging from Strength of attacks, to Skill, to armour and toughness of the defender. While deconstructing the original spreadsheet, it was taking me a long time to figure out what each cell reference in each formula meant. I would have to look up references like "C4" or "E20" and then go back to reading the original formula. This made it slow and error prone for me to read what the formulas were doing, and implement changes in an efficient and sustainable way.

In addition, if a new rule was implemented, I would need to manually implement that rule in every attack sequence in the spreadsheet. The original spreadsheet had a single attacker with 3 weapons attacking a single defender for a total of 3 attack sequences. I wanted to be able to handle everything from 11 weapons per attacker, to multiple attackers and defenders. Having to adjust formulas for each and every attack sequence individually was not an option.

### Goal: Lower the effort needed to create new use cases
When attempting to expand upon the original spreadsheet that I made a copy of, each sequence of attacks against the defender were coded on a cell by cell basis in an arrangement that didn't allow for easy copying or dragging of the formulas to create more attack sequence calculations. This made it challenging for me to expand the use case to questions like like "what about if and attacker with 11 weapons shoots a defender" or "which of these 3 attackers is most efficient against this defender?"

My goal for new use cases was for it to be as simple as collecting user inputs on the attacker and defender details, and then displaying the results of the attack sequences, without having to manage the calcluations themselves each time.

## Design Choices
The various design choices made were done with the intention of achieving the goals of increasing ease of maintenance, as well as lowering the effort of creating new use cases.

### Separate the front-end user interface from the back-end calculations
The front end user input and visualisation area was separated from the back end calculation area. The front end that the user interacts with serves as the area where they can make their inputs and view the results, but don't have to be overwhelmed or bombarded with the myriad of calculations that are done behind the scenes. Each front end can also be tailored specifically to meet the needs of specific use cases, and function independently of each other.

Consolidating all the calculations into the various back ends (dmg_calc and morale_calc) allowed a single point of implementation for each rule relating to attack sequences or morale. This would make it easier to maintain. Additionally, the back end is designed to accept a number of inputs in a specific structure (eg attacker strength, defender toughness etc) and generate outputs in a specific structure (number of models lost to damage etc). New use cases that are created simply need to submit their inputs into the relevant column structure on a particular row, and "pick up" their outputs in the respective columns of that same row. This drastically lowers the effort needed to implement use cases, as the calculations for attack sequences and morale are essentially "write once, call many times".

### Use ARRAYFORMULA for calculations
The ARRAYFORMULA function in Google sheets allows me to reference various columns in a table at once, and display the outputs in a new column. This obviates the need to drag formulas down through the rest of each column, preventing the possible error of forgetting to drag formulas, as well as providing a performance boost relative to having an individual formula in each row of the column. This drastically increases maintainability.

### Consolidate Keywords in a single tab
Weapon keywords such as "Rapid Fire", "Melee" and many others are all consolidated in a single tab called "Index", instead of having their strings written directly in formulas. This provides a central reference to review and maintain. If the wording of an ability or keyword is changed by Games Workshop, I can change the keyword here, rather than in every single formula that references it. This too makes the spreadsheet much easier to maintain.

### Use Named Ranges for column names
I made liberal use of the Google Sheets Named Ranges feature, which allows you to name a range, and subsequently refer to that range via its name instead of cell reference. For example, if "Weapon Strength" is in Sheet1 Column A, I could name Sheet 1 Column A "WEAPON_STRENGTH". This would allow me to refer to the column as "WEAPON_STRENGTH" rather than "Sheet1!A:A". This makes formulas much more readable, and the spreadsheet easier to maintain.

### Use BattleScribe data as a data source
BattleScribe is an app that allows for list building in various games such as Warhammer 40k. The list building rules and options (eg units, weapons etc) are community maintained and publicly available. Leveraging this community maintained data source would allow me to keep the spreadsheet up to date with changes to the points cost of units, or release of new units much more easily. This would drastically improve maintainability of the spreadsheet.

At present, I have only partially extracted weapon and unit profiles from the [BattleScribe data](https://github.com/BSData/wh40k). Developing this further is an ongoing project for me.


## Use cases
The Calculator has several use cases, each of which is designed to address various questions that are often asked during the process of building an army list. 

### Single Attacker split fire

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This use case attempts to answer the question "If I have this unit with a lot of guns, and I split its fire between these defenders, what is the points efficiency of this attacker?" Users can select a single attacker and up to eleven weapons to fire at each of up to two defenders. From my experience, units rarely have more than eleven weapons, but do commonly have more than three as provided in the original spreadsheet. With the ease of calculating as many attack sequences as needed, it was easy for me to allow for eleven weapons instead of three.

### Individual Attackers vs Defender

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/individual_attackers_vs_defender.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This tab allows a user to select up to three attackers and a defender. The points efficiency of each individual attacker against the defender is displayed in the charts at the top of the page.

After fleshing out the Single Attacker split fire tab, I found myself frequently switching between multiple attackers and their weapon loadouts to see which would be the most efficient against a given defender. This was essentially the question of "which of these attackers is most efficient against this defender?", which is a question that could directly be addressed by this use case. With this use case, the effectiveness of multiple attackers against the defender can be visualised side by side for easy comparison.

### Mixed Squad vs Individual Defenders

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/mixed_squad_vs_individual_defenders_numbered.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This tab in the spreadsheet allows users to configure a squad consisting of up to three different model types, and up to three different defenders. Charts at the top show how efficient the attacker squad is against each individual defender.

Often, after selecting a unit from the previous use case that I was keen to include in my army, I would be concerned how versatile this unit would be against multiple defender profiles. What if I brough an anti-tank specialist that was stellar against tanks, but my opponent didn't  bring tanks? How would this unit fare against infantry or heavy infantry instead? This use case allows users the ability to assess the effiency of an attacker against several individual defenders simulataneously.

In addition, many squads in the game usually have a "leader" unit such as a sergeant or an exarch, who has a slightly superior stat profile, and possibly a different weapon or equipment loadout. Allowing the user to configure an attacking squad as mixed (ie comprising of different models) would allow for more accurate assessment of the squad as a whole.

## What's next?
I've had a lot of fun creating this spreadsheet and using it to help me answer various questions of effectiveness and efficiency during the army list building process. Currently, I am working on a python script to  get a complete extract of the various unit and weapon profiles from the BattleScribe data. This will provide me a means to update the spreadsheet regularly with comprehensive data.

An upcoming project I am looking to undertake is a more programmatic calculation that pits every possible attacker against every possible defender, taking into account various possible loadouts and buff combinations. The results will be visualised in a public Tableau dashboard, where users can apply filters on attackers and defenders for dimensions such as faction, or presence/absence of a specific buff. I'm aware that a new edition is just around the corner, and that rules could drastically change within the next few months. Still, I do expect certain aspects of what I build in the current 9th edition to be reusable in 10th edition, such as the structure of BattleScribe data, and the general mechanics of the attack sequence.

I hope you enjoyed reading this content as much as I enjoyed creating it! Do check out the spreadsheet [here](https://www.gerardchan.com/projects/wh40k_9ed_attack_sim_sheet/) and share your feedback on what you'd like to see more of in the future!

---
layout: page
title: Warhammer 40k 9th Edition Attack Simulator Spreadsheet
description: A spreadsheet calculator to visualise attacker effectiveness in Warhammer 40k
img: assets/img/wh40k_9ed_attack_sim_sheet/dice.jpg
---

The Warhammer 40k 9th Edition Attack Simulator Spreadsheet is a spreadsheet designed to help players assess the effectiveness of various attacking units against various defending units.

Access it [here](https://docs.google.com/spreadsheets/d/1bh82RCG48618Yn82LHHmuk7gOLXqNdb-lyiQapqgCdA) and make a copy for yourself (File > Make a copy).

Do share your feedback on the calculator via the feedback form <a href="https://docs.google.com/forms/d/e/1FAIpQLSfY-DV-pBkGgVQsk72rUyJO-3VHsY2uJP1GpdpcA-a3Xqq3-w/viewform?usp=sharing">feedback form</a>.

## Contents
* This will become a table of contents (this text will be scrapped).
{:toc}

## Overview
The Warhammer 40k 9th Edition Attack Simulator Spreadsheet aims to help players assess the effectiveness of units against other units of their choice. In Warhammer 40k, it's important to build an army that is able to handle a variety of opposing units in an efficient and cost effective manner. By calculating the effectiveness of various attacking units against various defending units, and taking into account the impact of offensive and defensive buffs, this spreadsheet aims to help players select units for a well rounded army that is effectively able to tackle a variety of opposing units.

## Common Terms and Interface Elements
### Points Efficiency
Points Efficiency refers to how many points of damage the attacker deals to the defender in a single turn, relative to the points cost of the attacker. Both ranged and melee weapons can be used.

For example, an attacking unit costing 100 points attacks a 5-model unit of one wound defenders costing 20 points each (100 points total) and destroys 3 of them. The attacking unit would have destroyed 60 points of opposing models, while costing 100 points itself. This would result in a Points Efficiency of 60%.

### Attacker selection

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_selection.png" class="img-fluid rounded z-depth-1" zoomable=true %}

When selecting an Attacker, key in the number of models under "Qty" and select your model from the drop down menu under "Model". In most cases, it is easier to type the first few letters of your desired selection and then selecting your choice, than to scroll through the full list.

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_selection_dropdown.png" class="img-fluid rounded z-depth-1" zoomable=true %}

### Attacker Additional Points

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_points.png" class="img-fluid rounded z-depth-1" zoomable=true %}

In certain cases, units might have a per model or per unit cost that isn't captured in the base model cost or weapon cost. For example, Vanguard Veterans squads can take Jump Packs for 3 points per model. These costs can be entered in the Attacker Additional Points section. Unit and Per Model costs can be entered into their respective boxes. Capturing these costs will allow them to be factored in to the cost of the attacker unit in order to compute their Points Efficiency more accurately.

For Attackers, Weapons that cost additional points will be captured when selecting the weapon to attack with. 

### Attacker Modifiers

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_modifiers.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This section allows for the selection of a number of buffs or modifiers that might be applicable to the attacker. Buffs can be keyed in via one of several ways
- **Check Box**: Check or uncheck the box to toggle the modifier on or off
- **Drop Down**: Select an option from the drop down to select the appropriate setting for the modifer (eg Reroll to Hit has options for "None", "1's" or "All")
- **Input Box**: Such entries accept a numerical entry (eg entering "1" in the "6 to Wound Bonus AP" modifer means that rolls of 6 to Wound will have a bonus AP of 1)

### Defender Selection

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_defender_selection.png" class="img-fluid rounded z-depth-1" zoomable=true %}

When selecting a Defender, key in the number of models under "Qty" and select your model from the drop down menu under "Model". In most cases, it is easier to type the first few letters of your desired selection and then selecting your choice, than to scroll through the full list.

### Defender Points

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_modifiers.png" class="img-fluid rounded z-depth-1" zoomable=true %}

In certain cases, units might have a per model or per unit cost that isn't captured in the base model cost. For example, Vanguard Veterans squads can take Jump Packs for 3 points per model. These costs can be entered in the Defender Additional Points section. Unit and Per Model costs can be entered into their respective boxes. Capturing these costs will allow them to be factored in to the cost of the attacker unit in order to compute their Points Efficiency more accurately.

For Defenders with weapons that cost points, do add them to the Per Unit or Per Model inputs here, as the spreadsheet does not capture weapon loadouts for defenders.

### Defender Modifiers

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_defender_modifiers.png" class="img-fluid rounded z-depth-1" zoomable=true %}

This section allows for the selection of a number of buffs or modifiers that might be applicable to the defender. Buffs can be keyed in via one of several ways
- **Check Box**: Check or uncheck the box to toggle the modifier on or off
- **Drop Down**: Select an option from the drop down to select the appropriate setting for the modifer (eg Reroll to Hit has options for "None", "1's" or "All")
- **Input Box**: Such entries accept a numerical entry (eg entering "6" in the "Invuln Save" modifer means that the model(s) will be conferred a 6+ Invuln save)

### Attacker weapons

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_weapons.png" class="img-fluid rounded z-depth-1" zoomable=true %}

Attacker weapons can be selected using the drop down menu. Points Costs (if applicable) and Weapon Stats will automatically be looked up. Ranged Weapons will make a number of attacks based on their profile. Melee weapons will make a number of attacks based on the attacking models number of attacks, plus any bonus attacks conferred by the weapon.

In the case where attackers can choose which defenders to attack, the Weapon selection will be beside the defender to denote which defender is targetted. If the defender cannot be selected (eg when there is only a single defender, or attackers attack all defenders), the weapon selection will be beside the attacker.

### Attacker Attacks Input

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attacker_attacks_input.png" class="img-fluid rounded z-depth-1" zoomable=true %}

By default, attackers make their full number of attacks with melee weapons. However, in some cases you might want to make some (or none) of a model's melee attacks with one or more melee weapons. You can key in the number of attacks to make here. If you want to use none of a model's attacks with a weapon, key in 0. Bonus attacks granted by weapons will always be made, even in 0 is entered. For example, Astartes Chainswords have a bonus attack which will be executed even if 0 is entered into the Attacker Attacks Input.

### Attack Effectiveness Charts

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_attack_effectiveness_chart.png" class="img-fluid rounded z-depth-1" zoomable=true %}

Beside each Attacker Weapon is a series of Attack Effectiveness chart, denoting what proportion of attacks failed or succeeded in hitting, wounding, penetrating saves and shrugs. Green indicates the proportion of attacks that succeeded in that stage of the attack sequence. Red inidicates the proportion of attacks that failed that stage of the attack sequence. The greener the charts, the more effective the weapon was against the defender. Large amounts of red on the chart suggests that the weapon was not very effective against the defensive profile of the defender.

## Single Attacker split fire

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire.png" class="img-fluid rounded z-depth-1" zoomable=true %}

The Single Attacker split fire tab allows users to assess the effectiveness of a single attacker splitting fire against two different defenders. When attacking units have a large number of weapons (yes you, Repulsor Executioner), it might be prudent to split fire among multiple defenders to minimise damage lost to overkill, as well as to target each weapon to a defender profile that is most efficiently tackled with that weapon.

### Points Efficiency Chart

{% include figure.html path="assets/img/wh40k_9ed_attack_sim_sheet/single_attacker_split_fire_points_efficiency.png" class="img-fluid rounded z-depth-1" zoomable=true %}

The Points Efficiency Chart shows how many points of damage the attacker deals to the defender(s) in a single turn.

- Single Attacker split fire usage
    - Attacker input
    - Defenders input
    - defenders and attacker assessed all as one
    - charts (top and weapon level)
    - top groupings
- Indiv attackers vs defender usage
    - Attackers are individually assessed vs defender
    - top groupings
    - weapons on attacker row, all attack single defender
    - attacker row groupings
    - defender row grouping
- Mixed squad vs Individual Defenders usage
    - Defenders are individually assessed vs attacker squad
    - weapons of each attacker attack defenders in turn
    - attacker row groupings
    - defender row grouping
- Model Data
- Weapon Data
- Weapon costs

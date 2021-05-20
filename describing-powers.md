# Describing Powers

It's useful to have a machine-readable notation for describing a Hero system power that can easily be converted to a more human-readable representation for inclusion in documentation.

## Machine Notation

A power will be stored as a JSON object with the following keys:

* `displayName` &mdash; A display or role-play name for the power
* `basePower` &mdash; Description of the base power as an object containing:
    * `baseCost` &mdash; Number of character points to purchase the base power
    * `description` &mdash; Description of the power, _ex:_ `Blast 6d6`
* `adders` &mdash; An array of `Adder` objects, each consisting of:
    * `cost` &mdash; Number of character points to add to the cost
    * `description` &mdash; Description of the adder
* `advantages` &mdash; An array of `Advantage` objects, each consisting of:
    * `description` &mdash; Description of the advantage
    * `quarters` &mdash; The number of +¼ fractions to use to add to the cost
* `limitations` &mdash; An array of `Limitation` objects, each consisting of:
    * `description` &mdash; Description of the limitation
    * `quarters` &mdash; Number of -¼ fractions to use to reduce the cost

So, for example:

**Stargate:** Teleportation 100m, x32 Increased Mass; Area Of Effect (4m Radius; +1/4\*), Usable By Other (+1/4), Constant (+1/2), MegaScale (1m = 1,000 lightyears; +5) (875 Active Points); OAF Immobile (-2), Extra Time (1 Turn (Post-Segment 12), -1 1/4), Gate (6E1 301; -1/2), Can only travel to other Stargates (-1/2) (Real Cost: 167) **plus** END Reserve (87 END, 0 REC) (Real Cost: 22) &mdash; **Active Cost:** 897, **Real Cost:** 189

```json
{
  "displayName": "Stargate",
  "basePower": {
    "baseCost": 100,
    "description": "Teleportation 100m"
  },
  "adders": [
    {
      "cost": 25,
      "description": "x32 Increased Mass"
    }
  ],
  "advantages": [
    {
      "description": "Area of Effect 4m radius",
      "quarters": 1
    },
    {
      "description": "Usable By Other",
      "quarters": 1
    },
    {
      "description": "Constant",
      "quarters": 2
    },
    {
      "description": "Megascale 1m = 1,000 lightyears",
      "quarters": 20
    }
  ],
  "limitations": [
    {
      "description": "OAF Immobile",
      "quarters": 8
    },
    {
      "description": "Extra Time &mdash; 1 Turn (Post-Segment 12)",
      "quarters": 5
    },
    {
      "description": "Gate (see 6E1 301)",
      "quarters": 2
    },
    {
      "description": "Can only travel to other Stargates",
      "quarters": 2
    }
  ]
}
```

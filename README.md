# Implementer et Figma Design | Refleksion

Dette har været en sjov og udfordrende opgave, hvori jeg føler at jeg har udviklet mig meget og opdaget nye, smartere måder at organisere min CSS på.

En stor del af erfaringen er kommet af at benytte CSS nesting, som har givet mulighed for at gruppere design-elementer for på den måde at holde relevante styles yderligere samlet, og samtidig giver mulighed for at være endnu mere specifik ved brug af CSS-selectors indeni et scopet element.

Til at demonstrere dette, har jeg dette eksempel på hvordan jeg valgte at opsætte mit overordnede layout. Figma-designet er bygget op af afgrænsede sektioner med skarpe farveskift, der fylder hele skærmen, og derfor var det vigtigt at tænke dette ind i layoutet fra start. Til dette formål, opsatte jeg et grid med fleksible marginer, og sørgede for at alle direkte child-elements blev sat ind i “main”-kolonnen og nedarvede kolonnerne via subgrid.

![Layoutet i css.](/src/assets/images/progress/layout.png)

Når dette var gjort, kunne jeg opsætte en utility-class, der ville sætte et element til at spanne over hele skærmen om nødvendigt.

For at opsætte sektioner med farveskift, hvori farvepaletten bliver brugt til forskellige elementer af designer—f.eks. ombytning på tekstfarve og baggrundsfarve—har jeg benyttet data-themes som en attribut til at fortælle min css hvilket “farvetema” der skal benyttes på en given baggrund. Hver gang temaet skifter, bliver min custom css property automatisk opdateret.

En stor del af at gøre websiden responsiv lå i at udnytte grid og flexbox’s egne indbyggede funktioner til at få child-elements skubbet ned på næste række, når der ikke længere er plads til dem. Her er et eksempel fra oversigten over teamet på brug af auto-fill til at få browseren til selv at udregne hvor mange kolonner, der er plads til:

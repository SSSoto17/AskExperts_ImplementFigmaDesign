# Implementer et Figma Design | Refleksion

Dette har været en sjov og udfordrende opgave, hvori jeg føler at jeg har udviklet mig meget og opdaget nye, smartere måder at organisere min CSS på.

En stor del af erfaringen er kommet af at benytte CSS nesting, som har givet mulighed for at gruppere design-elementer for på den måde at holde relevante styles yderligere samlet, og samtidig giver mulighed for at være endnu mere specifik ved brug af CSS-selectors indeni et scopet element.

Til at demonstrere dette, har jeg dette eksempel på hvordan jeg valgte at opsætte mit overordnede layout. Figma-designet er bygget op af afgrænsede sektioner med skarpe farveskift, der fylder hele skærmen, og derfor var det vigtigt at tænke dette ind i layoutet fra start. Til dette formål, opsatte jeg et grid med fleksible marginer, og sørgede for at alle direkte child-elements blev sat ind i “main”-kolonnen og nedarvede kolonnerne via subgrid.

![Layoutet i css.](/src/assets/images/progress/layout.png)  
_Et fleksibelt layout i css, der tager højde for en main content kolonne og "breakout" elementer._

Når dette var gjort, kunne jeg opsætte en utility-class, der ville sætte et element til at spanne over hele skærmen om nødvendigt.

For at opsætte sektioner med farveskift, hvori farvepaletten bliver brugt til forskellige elementer af designet—f.eks. ombytning på tekstfarve og baggrundsfarve—har jeg benyttet data-themes som en attribut til at fortælle min css hvilket “farvetema” der skal benyttes på en given sektion. Hver gang temaet skifter, bliver min custom css property automatisk opdateret.

![Farvetemaer sat op med data-themes.](/src/assets/images/progress/colorthemes.png)  
_Farvetemaer sat op med data-themes._

![Et helt element bliver nemt ændret med variabler.](/src/assets/images/progress/colorthemesdemo.png)  
_Et helt element bliver nemt ændret med variabler._

En stor del af at gøre websiden responsiv lå i at udnytte grid og flexbox’s egne indbyggede funktioner til at få child-elements skubbet ned på næste række, når der ikke længere er plads til dem. Her er et eksempel fra oversigten over teamet på brug af auto-fill til at få browseren til selv at udregne hvor mange kolonner, der er plads til:

![Mit grid til cards'ne er sat op med grid auto-fill, så browseren automatisk sætter dem side om side når der er plads til dem, eller omvendt skubber dem ned på en ny række, når der ikke er.](/src/assets/images/progress/cardsrow.png)  
_Mit grid til cards'ne er sat op med grid auto-fill, så browseren automatisk sætter dem side om side når der er plads til dem, eller omvendt skubber dem ned på en ny række, når der ikke er._

![Her er kortene smalle og side om side.](/src/assets/images/progress/cardsrowdemo.png)  
_Her er kortene smalle og side om side._

Problemet med elementer, når de bliver skubbet ned på en ny række med færre kolonner, er at der ofte bliver mere plads til child-elementet, hvilket bryder designet og skaber en ubalanceret, ueffektiv brug af pladsen. Dette kan ikke nemt kontrolleres med en media query, da den kun tjekker for bredden på hele skærmen; men det er ofte, når en container bliver smallere at der kommer sådan et brud på designet—uafhængigt af om skærmen bliver større eller mindre.

En god løsning på dette er container queries. Her har jeg benyttet en container query på en wrapper rundt om hvert enkelt kort, så browseren kan holde øje med hvor bredt cardet bliver. Når det når over en hvis bredde, vil teksten blive skubbet op ved siden af billedet i stedet for at udnytte den overskydende plads bedre.

![I min container query kan jeg definere ændringer i layoutet på mit card, når det når over en bredde på 360px.](/src/assets/images/progress/cardscontainerquery.png)  
_I min container query kan jeg definere ændringer i layoutet på mit card, når det når over en bredde på 360px._

![Her har jeg brugt en container query på mine kort, så elementer lægger sig ved siden af hinanden når kortet bliver bredt.](/src/assets/images/progress/cardscontainerquerydemo.png)
![Her har jeg brugt en container query på mine kort, så elementer lægger sig ved siden af hinanden når kortet bliver bredt.](/src/assets/images/progress/cardscontainerquerydemo2.png)  
_Her har jeg brugt en container query på mine kort, så elementer lægger sig ved siden af hinanden når kortet bliver bredt._

Det har været en stor opgave at kode en hel hjemmeside med så mange nye redskaber, men også sjovt. Hvad jeg fandt mest udfordrende var at gennemskue, hvordan jeg bedst kunne udnytte disse nye properties mest effektivt og systematisk.

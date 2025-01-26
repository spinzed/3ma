Ovaj repozitorij sadrži pokazni projekt za kolegij 3D modeliranje i animacija na
Fakultetu elektrotehnike i računarstva, Sveučilište u Zagrebu.

## Opis projekta
Projekt je pokazna scena napravljena u Blenderu.
Izvorna datoteka projekta je `projekt.blend`, a renderirane scene se nalaze u
datotekama projekt_EEVEE.mkv i projekt_cycles.mkv, renderirane s Blenderovim renderim
EEVEE i Cycles.
U assets direktoriju se nalaze dodatni asseti koji se koriste pri renderiranju.

## Opis scene
Scena prikazuje šumu/travnjak s par stabala pokraj litice.
U centru pozornosti je lisica koja se nalazi iza dubla srušenog stabla.
Između uzbrdica u terenu teče potočić.
U jednom trenutku padne par kamenja s litice što privuče pozornost lisice
i preplaši pčele iz pčelinjaka.

## Tehnike implementiranja
- Teren: proceduralno generiran pomoću geometry nodeova iz vodoravno postavljene ravine.
Drvo je modelirano jednom te instancirano više puta pomoću InstanceOnPoints geometry nodea.
Trava je modelirana čestičnim sustavom (napomena: trava najviše ruši performance pa 
preporučujem ju onemogućiti u viewportu).
- Potočić: proceduralno generiran pomoću geometry nodeva iz bezierove krivulje.
Moguće je proizvoljno dodavati segmente krivulje i pomicati ih, potočić će biti projiciran
na teren i teći će u dobrom smijeru.
- Lisica: izrađena tehnikom low-poly modeliranja. Sadrži kostur generiran pomoću dodatka Riggify.
- Deblo: izrađeno kombinirano spajanjem 2 cilindra booleovim operacijama i skulpturiranjem.
- Litica: izrađena skulpturiranjem. Za kamenja koja padaju s litice koriste se RigidBody za
interakciju s terenom.
- Roj pčela: čestični sustav boida. Model pčele je skulpturiran.
Boid ima postavljenu opciju Boid Brain koja prati nevidljivi objekt koji se kreće po krivulji.

## Napomene
Asseti se nalaze u direktoriju `assets`.
Neke stvari nisu ispale kako sam zamislio, u budućnosti ću ih prepraviti.

Render pomopću Cyclesa ima vizualne pogreške, čini se da je problem u evaluaciji
geometry nodeaova prije renderiranja.
Još moram otkriti kako zaobići taj problem.

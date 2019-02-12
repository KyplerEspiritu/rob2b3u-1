# rob2b3u
Vélmenni II 
seinni áfangi í vélmennum þar sem nemendur byggja og forrita vélmenni
til að leysa hinar ýmsu þrautir
Í áfanganum leysa nemendur stórt verkefni sem nemendur hanna sjálfir með annað hvort VEX eða Arduino smátölvum. Nemendur gera verkáætlun þar sem verkefnið er brotið niður í minnstu einingar. Logskrár, verkefnalýsing, auðlindir þ.e vébúnaður og hugbúnaður sem þarf, flæðirit og sauðakóði og innleiðing. Öllu er steypt saman í lokaskýrslu .

# Verkefnalýsing
Við Ætlum að gera robot sem kastar rusl í ruslatunnu. Á meðan þú ert í tölvunni á robotinn að vera hliðin á þér á gólfinu. Þú gefur réttir robotinn ruslið sem þú vilt henda og ýtir á taka á fjarstýringunni sem framkvæmir ferlið. Við byrjum að hafa fasta staðsetningu fyrir ruslið og robotinn svo vélmennið veit nákvæmlega hvert það á að fara. Svo á það að geta farið þangað og hent ruslinu í tunnuna.

Næsta project er að láta robot fara í "sound mode". Þegar það er slökkt á ljós (eða ýtt á takka), þá getur robot annaðhvort farið í "party" mode eða "sleep" mode. Í party mode, kveikir hann á öllum LED (kannski RGB LED með rainbow litum), og spilar partý tónlist. Hann dansar líka. Í sleep mode, slekkur hann á öllum LED'dum(eða lætur ljós blikkahægt og rólega) og spilar rólega tónlist(eða enga tónlist). Það á líka að vera hægt að stilla vekjaraklukku fyrir morgundaginn. Við utlum að nota Raspberry Pi sjá um ljósin, við munum þá nota auka batterí til þess að sjá um það. Við munum nota relay til þess að stjórna ljósunum. Ljósin sem við ætlum að nota er bara hreinlega marglita led seríur, 40 ljósa fyrir party mode og 10 ljósa led seríur fyrir sleep mode. Fyrir sleep mode munum við reyna að láta ljósið blikka hægt og rólega. Við munum nota relayið til þess að skipta ljósunum á milli party mode og sound/sleep mode. Það sem við höfum áhyggjur af er þegar vélmennið er í sleep mode og er að blikka ljósið, heyrist klikk hljóð í relayinu þegar það er að skipta um channel, en við munum redda því þegar það kemur að því, ef ekki látum við það vera. 

Við viljum líka láta vélmennið elta ljós. Við verðum með vasaljós eða notum ljósið í símanum og notum það til að láta vélmennið elta okkur. Þetta gæti verið vandamál út af við utlum að henda helling af ljósum af öllum litum á vélmennið fyrir "party" mode þannig við utlum að reyna láta vélmennið elta skærsta ljósið. Erum ekki alveg vissir hvort það er hægt en utlum að prófa.

Robotinn á einnig að geta leikt sig við notandan. Við utlum að vera með switch á robotinn þannig þegar þú færir það, mun vélmennið færa það til baka. Vélmennið á að vera með helling af hegðunnir til að gefa vélmennið smá líf.

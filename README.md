# krepsinio-treniruoklis-iot
Krepšinio pataikymų skaičiavimo IoT prototipas su ESP8266 ir Blynk
Krepšinio treniruoklis: IoT sistema

Šis projektas – paprastas IoT principu veikiantis krepšinio treniruoklis, kuris automatiškai fiksuoja pataikymus į krepšį ir rezultatą realiu laiku rodo mobiliojoje programėlėje, naudojant **ESP8266 NodeMCU** ir **Blynk Cloud** platformą.


---

## Pagrindinės funkcijos

- Pataikymo į krepšį fiksavimas naudojant **IR jutiklį**.
- Automatinis **taškų skaičiavimas** ir jų saugojimas valdiklyje.
- **LED indikacija** kiekvieno sėkmingo pataikymo metu.
- Rezultato siuntimas į **Blynk Cloud** ir rodymas **Android/iOS** programėlėje.
- Paprasta **debounce** logika, neleidžianti tą patį metimą suskaičiuoti kelis kartus.

---

## Sistemos architektūra

Sistema sudaryta iš trijų pagrindinių sluoksnių:

1. **Jutiklių lygmuo**
   - IR modulis (siųstuvas + imtuvas) po krepšio lanku.
   - LED indikatorius su rezistoriumi.

2. **Valdymo lygmuo**
   - ESP8266 NodeMCU vystymo plokštė.
   - Kodo logika: pataikymų skaičiavimas, debounce, LED valdymas.

3. **Debesijos ir vartotojo sąsaja**
   - Blynk Cloud (virtualus PIN taškų reikšmei).
   - Blynk mobilioji programėlė telefone.

Duomenų kelias:
> Kamuolys kerta IR spindulį → signalas perduodamas į ESP8266 → padidinamas taškų skaičius → trumpam įjungiamas LED → nauja reikšmė nusiunčiama į Blynk → programėlė telefone atnaujina rezultatą realiu laiku.

---

## Naudota įranga

| Komponentas                    | Kiekis | Pastabos                               |
|--------------------------------|--------|----------------------------------------|
| ESP8266 NodeMCU                | 1      | Valdiklis su integruotu Wi-Fi         |
| IR siųstuvas + imtuvas         | 1 rinkinys | Pataikymo fiksavimui                 |
| LED (5 mm)                     | 1      | Vizualinė indikacija                  |
| Rezistoriai (pvz. 220 Ω, 10 kΩ)| keli   | LED ir signalo stabilizavimui         |
| Breadboard                     | 1      | Prototipavimui                         |
| Jungiamieji laidai             | -      | Valdiklio ir jutiklių sujungimui      |
| 5 V maitinimo šaltinis / USB   | 1      | Sistemos maitinimui                   |

Orientacinė komponentų kaina prototipui: **~13,50–15 €**.

---

## Naudota programinė įranga

- **Arduino IDE** – kodo rašymui ir įkėlimui į ESP8266.
- **Blynk IoT**:
  - Blynk Cloud – duomenų priėmimui ir saugojimui.
  - Blynk mobilioji programėlė (Android / iOS) – rezultatų atvaizdavimui.

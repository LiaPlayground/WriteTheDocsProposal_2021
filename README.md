<!--
author:   André Dietrich

email:    LiaScript@web.de

version:  0.0.2

language: en

narrator: US English Female

date:     10th of June

logo:     https://upload.wikimedia.org/wikipedia/commons/thumb/c/cb/Bottega_di_marinus_van_reymerswaele%2C_due_esattori_delle_tasse%2C_1540-50_ca._05_libro.jpg/640px-Bottega_di_marinus_van_reymerswaele%2C_due_esattori_delle_tasse%2C_1540-50_ca._05_libro.jpg

comment:  Pitch-Talk about LiaScript for the "EMEA Write the Docs Proposals
          Workshop and Discussion" Meetup.

import: https://raw.githubusercontent.com/liaTemplates/AVR8js/main/README.md

-->

[![LiaScript](https://raw.githubusercontent.com/LiaScript/LiaScript/master/badges/course.svg)](https://liascript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/WriteTheDocsProposal_2021/main/README.md)

# Next-Gen Interactive Docs


|         | André Dietrich                                   |
|:------- |:------------------------------------------------ |
| Twitter | [\@an_dietrich](https://twitter.com/an_dietrich) |
| email   | [LiaScript\@web.de](mailto:LiaScript@web.de)     |
| GitHub  | https://github.com/liascript                     |

---

Presentation: https://github.com/LiaPlayground/WriteTheDocsProposal_2021

[qr-code](https://LiaScript.github.io/course/?https://raw.githubusercontent.com/LiaPlayground/WriteTheDocsProposal_2021/main/README.md)


## LiaScript

Website: https://LiaScript.github.io

**LiaScript is not a tool, it is a Markup language based on three design principles:**


1. Holistic: One format for different purposes

2. Simple & textbased: Due to a smart interpreter

3. Interactive: Scripting should be an essential part of publishing

### 1. Holistic

{{1}} **Responsive**

                    --{{1}}--
The output should of course be responsive to be consumable on different devices.


{{2}} **Rendered in various ways {3}{textbook/presentation/slides}**

                    --{{2}}--
It should be possible for the end-user to decide in what format she or he wants
to digest the content.

                    --{{3}}--
LiaScript currently supports three different formats.


{{4}} **Narrative & Multilingual**


             --{{4 Russian Female}}--
Первоначально создан в 2004 году Джоном Грубером (англ. John Gruber) и Аароном
Шварцем. Многие идеи языка были позаимствованы из существующих соглашений по
разметке текста в электронных письмах...

### 2. Simple & Textbased

                 {{1-2}}
!?[video](https://www.youtube.com/watch?v=bICfKRyKTwE)


                 {{2-3}}
                                    Multiline
    1.9 |
        |                  *
      y |               *     *
      - | r r r r r r r*r r r r*r r r r r r r
      a |             *         *
      x |            *           *
      i | B B B B B * B B B B B B * B B B B B
      s |         *                 *
        | *  * *                       * *  *
     -1 +------------------------------------
        0              x-axis               1


                 {{3-4}}
| Animal          | weight in kg | Lifespan years | Mitogen |
| --------------- | ------------:| --------------:| -------:|
| Mouse           |        0.028 |             02 |      95 |
| Flying squirrel |        0.085 |             15 |      50 |
| Brown bat       |        0.020 |             30 |      10 |
| Sheep           |           90 |             12 |      95 |
| Human           |           68 |             70 |      10 |


                  {{4}}
********************************************************************************

Do you like this approach so far?

    [[ ]] No?
    [[X]] Yes of course!
    [[X]] ... not sure ...
    [[X]] ... not sure ...
    [[ ]] ... not sure ...

********************************************************************************

### 3. Interactive Scripting

    {{|>}}
The sum of
<script output="a" default="1" input="range">@input</script>
and
<script output="b" default="1" input="number">@input</script>
is
<script>@input(`a`) + @input(`b`)</script>.


#### Data-driven publishing
<!--
sin: <script format="number"
             localeStyle="currency"
             currency="EUR"
             locale="de-DE"
             modify="false"
    > Math.sin(@input(`a`) + 0.5 * @0) </script>
-->

Just an arbitrary value <script output="a" default="1" input="range">@input</script>, right???


<!-- data-type="line" -->
| Header 1 | <script>@input(`a`)</script> |
|:-------- | ----------------------------:|
| 1        |                      @sin(1) |
| 2        |                      @sin(2) |
| 3        |                      @sin(3) |
| 4        |                      @sin(4) |
| 5        |                      @sin(5) |
| 6        |                      @sin(6) |
| 7        |                      @sin(7) |
| 8        |                      @sin(8) |
| 9        |                      @sin(9) |


#### Coding++

https://github.com/LiaTemplates/AVR8js

``` cpp
void setup() {
  Serial.begin(9600);
}

void loop() {
   while (Serial.available() > 0 ) {

     String str = Serial.readString();

     if (str.equals("send")) {
        Serial.println("identified");
     } else {
        Serial.println("unknown");
     }
   }
}
```
@AVR8js.sketch


<div id="example">
<wokwi-led color="red"   pin="13" label="13"></wokwi-led>
<wokwi-led color="green" pin="12" label="12"></wokwi-led>
<wokwi-led color="blue"  pin="11" label="11"></wokwi-led>
<wokwi-led color="blue"  pin="10" label="10"></wokwi-led>
<span id="simulation-time"></span>
</div>

``` cpp
byte leds[] = {13, 12, 11, 10};
void setup() {
  Serial.begin(115200);
  for (byte i = 0; i < sizeof(leds); i++) {
    pinMode(leds[i], OUTPUT);
  }
}

int i = 0;
void loop() {
  Serial.print("LED: ");
  Serial.println(i);
  digitalWrite(leds[i], HIGH);
  delay(250);
  digitalWrite(leds[i], LOW);
  i = (i + 1) % sizeof(leds);
}
```
@AVR8js.sketch(example)

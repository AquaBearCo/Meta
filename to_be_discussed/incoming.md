De dingen die ik heb aan te merken zijn deels al besproken:
 - Of het document ook op gaat voor QML. Dat doet het dus, maar met de uitzondering dat members in lowerCamelCasing worden gedaan om in sync te zijn met ingebouwde members van QML.
 - Dat commentaar niet gebruikt moet worden om uit te leggen wat er gaat gebeuren. Ik zie dat je dat al hebt aangepast en nu ben ik het er mee eens.

Verder is er nog een ding niet ter sprake gekomen vanwege tijdsgebrek:
 - Dat functies niet meer dan 7-10 regels code mogen bevatten. Vaak is de input checking alleen al 7-10 regels. Ik vind de richtlijn dat het op een scherm moet passen hier weer een goede, maar zelfs dan is het soms nodig om daar van af te wijken. Neem bijvoorbeeld weer het voorbeeld van in Uranium: UM/Math/Polygon.py Polygon::intersectionConvexHulls(...), waar een vrij ingewikkelde loop in zit over twee variabelen tegelijk. Om het op te breken in stukjes zou de code minder navolgbaar maken omdat je continu naar boven en beneden zou scrollen, en vrijwel de hele context meegekopiëerd moet worden.


Nog meer code conventie suggesties:
- Taal engels, zowel voor variabele-namen als commentaar. Ter discussie: en-US of en-UK  (color/colour, finalize/finalise, etc).
- Volgorde van parameters in functies: input - output - optional (note: memcpy in C is output - input).

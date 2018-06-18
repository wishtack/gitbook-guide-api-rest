# Datetime

Comment échanger les dates et heures avec les APIs ?

Nous n’utiliserons pas le terme "timestamp" afin éviter les conflits avec le "unix timestamp".

Pas de débat à ce sujet, **ISO 8601** est là depuis 1997 :

* [https://www.w3.org/TR/NOTE-datetime](https://www.w3.org/TR/NOTE-datetime)
* [https://www.iso.org/obp/ui\#iso:std:iso:8601:-2:dis:ed-1:v1:en](https://www.iso.org/obp/ui#iso:std:iso:8601:-2:dis:ed-1:v1:en)
* `1997-07-16`
* `1997-07-16T19:20:01.003Z`

{% hint style="success" %}
Simplifiez la vie de vos clients en convertissant les “datetimes” en UTC.
{% endhint %}




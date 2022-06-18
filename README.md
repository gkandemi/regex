# Regular Expressions | Regex | Düzenli İfadeler

![Düzenli ifadeler (Regular Expressions | #Regex) Nedir? Nasıl Kullanılır? #JavaScript ile Regex](https://i.ytimg.com/vi/bF_zEzFQZuA/maxresdefault.jpg?v=5fea5ba1)

Bu doküman [Kablosuzkedi](https://www.youtube.com/kablosuzkedii) Youtube kanalı için hazırlanmıştır. İsterseniz aşağıdaki linkten dersi izleyebilirsiniz :)

[Düzenli ifadeler (Regular Expressions | #Regex) Nedir? Nasıl Kullanılır? #JavaScript ile Regex](https://youtu.be/bF_zEzFQZuA)

Eveeett, geldik malum konuya. Regex bize herşeyden önce bir karakter seçim izni verir. Bu karakter veya karakter grubu tamamen sizin bakış açınıza göre değişir.

## Flags

```
/g match All
/m multiline
/i case sensitive
/u unicode
```

## Nicelikler / Notasyonlar

### + (one or more)
Bir tane veya şarta uyan birden fazla karakteri tek bir ifade olarak seçer.

```
Aloooo burada ne oluyor acaba?
```

gibi bir cümlede

```
o+
```

yaparsak bize

Al**oooo** burada ne **o**luyor acaba?

ifadelerini dönecektir.

### ? Opsiyonel karakter

Opsiyonel olan karakterleri işaretlememiz için kullanılır

```
Aloooo burada ne oluyor acaba?
```

gibi bir cümlede

```
o+r?
```

yaparsak bize

Al**oooo** burada ne **o**luy**or** acaba?

ifadelerini dönecektir. Burada **o+** dediğimiz için **oooo** olarak bize eşleşmenin tamamını verdi.

### \* (zero or more) | ? ve + Birleşimi

**\+** ve **?** birleşimidir. Opsiyonel olarak mümkün olan eşlesmeyi yine birleşim olarak alir.

```
Aloooo burada ne oluyor acaba?
```

gibi bir cümlede

```
o+r*
```

yaparsak bize

Al**oooo** burada ne **o**luy**or** acaba?

ifadelerini dönecektir. Çünkü burada **\*** karakterinin özelliğinden dolayı **r** opsiyonel olarak konumlandırılır. Eğer varsa da **o** ve **r** birleşimi olarak ele alacaktır.

### \. (nokta) Notasyonu
öncesindeki ya da sonrasindaki yeni satır hariç herhangi bir karakteri temsil eder.

```
Aloooo burada ne oluyor acaba? Yeni video geldi.
Bence güzel bir video olmuş
```

```
d..
```

yaparsak bize

Aloooo bura**da** ne oluyor acaba? Yeni vi**deo** gel**di.**
Bence güzel bir vi**deo** olmuş

ifadesini geri dönecektir. Eğer buna bir tane daha **\*(.) nokta** koyarsak

```
d...
```

şeklinde bu sefer seçim

Aloooo bura**da n**e oluyor acaba? Yeni vi**deo** gel**di.**
Bence güzel bir vi**deo** olmuş

ifadesini geri dönecektir.

##### Fakat Nokta karakterini aramak istersek bu durumda;

**\\.** ile escape yaparak nokta karakterini arayabiliriz.

### \w

Boşluk olmayan tüm karakterleri teker teker seçer.

### \W negatif versiyon (\w)

\w' nin tersidir. Sadece boşlukları teker teker seçer.

### \s

Boşlukları seçerl

### \S Negatif versiyon (\s)

\s' in tersidir. Boşluklar harici tüm karakterleri teker teker seçer.

### \d Sayılar

Sayıları seçer

### \D Sayı olmayanlar

Sayı olmayan karakterleri seçer.

## Aralık belirleme

### \{x,y}
**x** karakterden oluşan bir kelime grubu seçer.
**y** belirtilmek zorunda değildir. eğer belirtilmezse x ve daha fazlasi olarak yorumlanır

```
\w{4,}
```

4 karakterden fazla olan kelimeleri sec.

## Karakter Gruplama [fc]at
Başı f **ya da** c ile başlayan **"at"** ile biten kelimeler.
Aynı zamanda karakter gruplamayı bir aralık belirleme için de kullanabiliyoruz. Mesela **a** ile **z** arasındaki tüm karakterler gibi.

```
fat cat hat tat nat Fat Cat 4at 5at
```

```
[a-tA-T0-5]at
```

### Aralık Belirleme

```
[a-z] [A-Z] [a-zA-Z] [0-9] [a-f]
```

gibi..

```
[a-zA-Z]at
```

## Gruplama İşlemi (...)

Sadece 1 karakter degil birden fazla karakteri grup şeklinde almayi saglar
(t|T)he başındaki karakter t ya da T olabilir sonu he ile biter..

```
The fat cat ran down the street.
```

```
(t|e|r){2,3}\.
```

içerisinde t veya e veya r geçen ve sonunda "." ile biren en az 2 en çok 3 karakterlik kelime gruplarini seç.

Bu bize **eet.** ifadesini verecektir.

```
rerere rarara bir şeyler şampiyon
```

buradan re{2,3} üzerinden ilerleyeceğiz.

```
(re|ra){2,3}
```

içerisinde en az 2 en cok 3 "re" olan kelime gruplarini sec

```
rere gibi ya da rerere
```

### ^ Satır başındaki karakteri belirleme

```
Sokakta yalnız yürüyorum.
sokak bunun farkında bile değil.
```

```
^[Ss]okak
```

satır başı T veya t ile başlayan he ile biten karakter gruplarını seç!

### \$ Satır sonundaki karakteri belirleme

```
\.$
```

sonu nokta ile biten ifadeler.

## Lookahead

Belirlediğimiz karakter ya da karakter gruplarıyla **devam eden** yada **devam etmeyen** ifadeleri seçmemizi sağlar

```
ifade(lookahead)
```

şeklinde düşünülebilir. 2 farklı yöntemi vardır.

### Pozitif Lookahead | Seç - ?=

Negatif Lookahed'in tam tersidir. Belirlediğimiz karakter ile devam **eden** ifadeleri seçer. Mesela q ile başlayıp u ile devam **eden** bir ifadeyi seçmek istersek

```
quantity and qrcode is really useful
```

```
q(?=u)[a-zA-Z0-0]+
```

şeklinde bir ifade yazılabilir. Buranın açıklmaası ise **q** ile başlayıp **u** ile devam eden kelime grubunu seç demektir.

Yine aynı metinden yola çıkarak **u** ile devam eden karakterleri **seç** demek istersek

```
.(?=u)
```

bu bize **q** ve **boşluk** ve **f** karakterlerini seçecektir.

##### Farklı bir örnek

```
The fat cat ran down the street. rere
```

ifadesinden **at** ile **devam eden** karakterleri seç demek istersen

```
.(?=at)
```

bu ifade bize **f** ve **c** karakterlerini verir. Çünkü cümle içerisinde **at** ile devam eden sadece **fat** ve **cat** vardır

burada f ve c yi alır.

### Negatif Lookahead | Seçme - ?!

Belirlediğimiz karakter ile devam etmeyen ifadeleri seçer. Mesela q ile başlayıp u ile devam etmeyen bir ifadeyi seçmek istersek

```
quantity and qrcode is really useful
```

```
q(?!u)[a-zA-Z0-9]+
```

burada q ile başlayıp u ile **devam etmeyen** kelime grubunu seçer. [a-zA-Z0-9] ile herhangi bir karakteri gidebildiği karar seçmesini sagladik bu bize **qrcode** kelimesini geri döndürecektir.

```
q(?!r)[a-zA-Z0-9]+
```

Eğer bu ifadeyi **u** yerine **r** ile değiştirirsek yani q ile başlayıp r ile devam **etmeyen** kelime grubunu seç dersek bu durumda **quantity** seçilecektir.

Yine aynı metinden yola çıkarak **u** ile devam eden karakterleri **seçme** demek istersek

```
.(?!u)
```

bu bize **q** ve **boşluk** ve **f** hariç diğer tüm karakterleri seçecektir.

##### Farklı bir örnek

```
The fat cat ran down the street
```

kelimesinden at ile **devam etmeyen** tüm karakterleri seç demek istersen

```
.(?!at)
```

burada **f** ve **c** hariç hepsini **teker teker seçer** çünkü seçici olarak (.) nokta kullanılmıştır.

## Look Behind

Öncesinde belirlediğimiz karakter ya da karakter gruplarıyla **devam eden** yada **devam etmeyen** ifadeleri seçmemizi sağlar

```
(lookabehind)ifade
```

### Pozitif Look Behind | Seç - ?<=

Seçeceğimiz ifadelerin **öncesindeki** karakter ve karakter grubunun **olup olmamasını** kontrol eder. Böylece öncesinde **şu varsa bunu seç** gibi bir seçim yapma durumuna imkan verir.

```
quantity and qrcode is really unuseful but this is an unethical
```

böyle bir cümlede **un** ile başlayan karakterleri seçelim.

```
(?<=un).
```

quantity and qrcode is really un**u**seful but this is an un**e**thical

karakterlerini verecektir. Çünkü öncesinde **un** karakterleri bulunmaktadır.

##### Farklı bir örnek

```
quantity and qrcode is really unuseful but this is an unethical. The man was born in early age. Also the man is really old
```

cümlesinde almak istediğimiz kelimeler **punisher** ve **man** kelimeleri olsaydı. Bunun öncesinde The var mı yok mu diye kontrol edebilirdik. Diğer bir bakış açısı ise The veya the ile başlayan kelimeleri bana nasıl getirebilirdik? olabilir. Bunun için

```
(?<=[tT]he )[a-zA-Z]+
```

ifadesi bizim için yeterli olacaktır. Çünkü The ya da the bizim seçmek istediğimiz iki farklı kelime olduğu için burada T veya t opsiyonel olmalıdır. Bu ifade bize şunu **punisher** ve **man** kelimelerini verecektir.

### Negatif Look Behind | Seçme - <?!

Pozitif look behind'ın tam tersidir. Pozitif look behind **seçim yaparken**, negatif içe öncesindeki karakter veya karakter grubunun olması durumunda devam eden ifadeyi **seçmez**.

```
quantity and qrcode is really unuseful but this is an unethical
```

böyle bir cümlede **un** ile başlayan karakterleri **seçmeyelim**.

```
(?<!un).
```

**quantity and qrcode is really un**u**seful but this is an un**e**thical**

karakterleri haricindeki tüm karakterleri verecektir. Çünkü öncesinde **un** karakterleri bulunmaktadır.

##### Farklı bir örnek

```
quantity and qrcode is really unuseful but this is an unethical. The man was born in early age. Also the man is really old
```

cümlesinde **öncesinde** **The** veya **the** olmayan tüm karakterleri seç demek istersek

```
(?<![Tt]he ).
```

ifadesi bizim için yeterli olacaktır. Çünkü The ya da the bizim seçmek istediğimiz iki farklı kelime olduğu için burada T veya t opsiyonel olmalıdır. Bu ifade bize;

**quantity and qrcode is really unuseful but this is an unethical. The** p**unisher was born in early age. Also the** m**an is really old**

ifadesini verir. Çünkü The veya the ile devam eden karakterler **p** ve **m** karakterleri. Bu karakterler haricindekilerin tamamını seçecektir.

## Örnekler

### Telefon Numarası Seçmek

```
1234567890
123-456-7890
123 456 7890
(123) 456-7890
+1 123 456 7890
```

```
\d{3}[ -]?\d{3}[ -]?\d{4}
```

```
(?<areacode>\d{3})[ -]?(?<inital>\d{3})[ -]?(?<deneme>\d{4})
```

```
\(?(?<areacode>\d{3})\)?[\) -]?(?<inital>\d{3})[ -]?(?<deneme>\d{4})
```

```
(\+\d{1}[ -])?\(?(?<areacode>\d{3})\)?[ -]?(?<inital>\d{3})[ -]?(?<deneme>\d{4})
```

```
(?:(\+\d{1})[ -])?\(?(?<areacode>\d{3})\)?[ -]?(?<inital>\d{3})[ -]?(?<deneme>\d{4})
```

```
(?:(\+\d{1})[ -])?\(?(?<areacode>\d{3})\)?[ -]?(?<inital>\d{3})[ -]?(?<deneme>\d{4})
```

```
(?<area>(\+\d{1,}))[ -]?\(?(?<operator>\d{3})\)?[ -]?(?<main>\d{3})[ -]?(?<number>\d{4})
```

```
((?<area>\+\d{1,2})[ -])?\(?(?<operator>\d{3})\)?[ -]?(?<main>\d{3})[ -]?(?<number>\d{4})
```

**Video içerisinde yapılan**

```
(?<areaCode>\+\d{2})?[ ]?\(?(?<operator>\d{3})\)?[ -]?(?<main>\d{3})[ -]?(?<number>\d{4})
```

### Tarih Validasyonu

```
14/02/2018
14-02-2018
14.02.2018
14.02.18
```

```
(?<day>([0-9]{2}))([\/\-\.])(?<month>([0-9]{2}))([\/\-\.])(?<year>([0-9]{2,4}))
```

**Video içerisinde yapılan**

```
(?<day>\d{2})[\/\-\.](?<month>\d{2})[\/\-\.](?<year>\d{2,4})
```

##### ÖDEV

```
2018/02/14
2018-02-14
2018.02.14
18.02.14
```

### [url~title] içerisinden bilgileri almak

```
[https://www.videosinif.com~videosinif]
[https://www.kablosuzkedi.com,kablosuzkedi]
[https://www.youtube.com/kablosuzkedi|kablosuzkedi youtube kanalı]
```

İlk olarak URL kısmını alalım

```
(?<=\[)(.*)(?=~)
```

pozitif **look behind** ve pozitif **look ahead**

```
(?<url>((?<=\[)(.*)(?=~)))
```

URL'yi gruplayarak ayıralım

```
(?<title>(?<=~)(.*)(?=\]))
```

title bilgisini de gruplayarak alabiliriz.

```
(?<url>((?<=\[)(.*)(?=[~|\,|\|])))[~\,\|](?<title>(?<=[~|\,|\|])(.*)(?=\]))
```

```
(?<url>(?<=\[)(.*)(?=[~,\|]))[~|,|\|](?<title>(?<=[~|,|\|])(.*)(?=\]))?
```

**Video içerisinde yapılan**

```
(?<=\[)(?<url>.*)(?=[~,\|])[~,\|](?<=[~,\|])(?<title>.*)(?=\])
```

Bu iki ifadenin de ayni gruplarda toplanabilmesi için araya ~ ekleyerek tüm ifadeyi seçtiriyoruz.

### Key: value Çiftini almak

```
Name: Gokhan
LastName: Kandemir
Address: Adana
Age: 33
Married: Yes
```

```
(?<fieldName>^[a-zA-Z]+): (?<value>[a-zA-Z0-9]+)
```

### Web Sayfasından linkleri almak

```
<a(\s+)href="(?<url>([^"]*))"
```

```
<img(\s)+src='[^']*'
```

[^'] => ' olmayan tüm karakterleri seç

### \<body>...\</body> içerisindeki içeriği almak.

```
<body[^>]*>([\w|\W]*)<\/body>
```

### Email Validasyonu

```
gokhan@gkandemir.com adresinden güzel bir email aldim. peki bu .com uzantılı email adreslerinden çektiğimiz nedir be kardeşim. onunla beraber delphixdfd@gmail.com diye ayri bir ergen zamanlarimda aldigim email adresi de mevcut :D
```

```
([a-zA-Z0-9])+\@([a-zA-Z0-9])+\.[a-zA-Z]{2,}
```

**Video içerisinde yapilan.**

```
\w+@\w+\.[a-zA-Z]{2,}
```

### URL Validasyonu

```
burada bir ton web sayfası var. https://www.google.com bunlardan bir tanesi. Neden olduğunu bilmiyorum ama http://www.test123.space de bunlardan bir tanesi. Oldukça güzel bir web sayfası daha var burada www.kablosuzkedi.com uzun zamandan beri güncellenmemiş fakat yine de bilgiler işe yarayabilir. Fakat video izlemek isterseniz youtube.com da buna uyan diğer bir güzel web sayfası
```

```
(https?:?\/\/)?(www)?\.?[a-zA-Z0-9]+\.[a-zA-Z]{2,}
```

**Video içerisinde Yaptığımız örnek**

```
(https?:\/\/)?(www\.)?([a-zA-Z0-9]+)(\.[a-zA-Z]{2,})
```

### Hashtag Ayıklamak

```
Regex için video hazırlıyorum. #Regex ile çözümlemek için Bana uğraştığınız merak ettiğiniz metinleri yazabilir misiniz? Mesela #Web sayfasındaki <body></body> #tag 'leri arasındaki bilgileri almak gibi. Bu #kolay tabi :) #Derdımianlatabilmişimdirumarim :) #360dayscleancode
```

```
#[a-zA-Z0-9işüğçöı]+
```

### Youtube, Vimeo, İzlesene Video URL Ayıklama

```
data-config-url="https://player.vimeo.com/video/488734703/config?autopause=1&amp;autoplay=1&amp;byline=0&amp;collections=1&amp;context=Vimeo%5CController%5CClipController.main&amp;default_to_hd=1&amp;outro=nothing&amp;portrait=0&amp;share=1&amp;title=0&amp;watch_trailer=0&amp;s=8be48fe12cfacadb79085e9c2acbd6568c1fb641_1609112069" data-fallback-url="//player.vimeo.com/video/488734703/fallback?js"

ZeroMQ nedir isimli video şu an yayında! https://www.youtube.com/watch?v=YAYp7hbOu7o

Pentagram'ın güzel bir şarkısı güzel bir şarkı gibi sanki ama eski tadını vermiyor https://www.izlesene.com/video/pentagram-bu-duzen-yikilsin/10523935
```

```
(https:\/\/)(www\.)?(?<vimeo>(player\.vimeo\.com\/video\/[0-9]+\/)?)(?<youtube>youtube\.com\/watch\?v=[a-zA-Z0-9]+)?(?<izlesene>(izlesene\.com\/video\/[a-zA-Z0-9\/-]+))?
```

## JavaScipt ile Yaptığımız Kodlar

#### JavaScript ile E-mail Validasyonu

```
const email_regex = /\w+@\w+\.[a-zA-Z]{2,}/g;
if (email_regex.test("gokhan@gkandemir.com")) {
    alert("Başarılı");
} else {
    alert("Başarısız")
}
```

#### JavaScript ile Hashtag Listesini Almak

```
const regex = /#[a-zA-Z0-9şığüçö]+/gm;

const str = `Regex için video hazırlıyorum. #Regex ile çözümlemek için Bana uğraştığınız merak ettiğiniz metinleri yazabilir misiniz? Mesela #Web sayfasındaki <body></body> #tag 'leri arasındaki bilgileri almak gibi. Bu #kolay tabi :) #Derdimianlatabilmişimdirumarım :) #360dayscleancode`;

// console.log(str.match(regex));

str.match(regex).forEach(h => console.log(h));
```

Son olarak isterseniz bu [link üzerinden](https://cs.lmu.edu/~ray/notes/regex/) Regex örneklerini inceleyerek kendinizi test edebilirsiniz. Oldukça faydalı olduğunu söyleyebilirim :)

# HEX <-> Int

## Загальна інформація 
Для обчислень дані зберігаються у окремих осередках, кожна у тому числі зберігає байт (8 біт). Для окремого значення, що перевищує 8 біт – ми можемо зберігати його як послідовність байтів. При цьому важлива послідовність, в якій ми зберігаємо байти (залежить від системи, що використовується). Іноді використовується збереження молодшого байта в першу комірку пам'яті, а старший байт в останню. Іноді навпаки. В даному випадку важливо як ми перетворимо шістнадцяткове (hex) значення на ціле беззнакове значення.

![Big and Little Endian](https://i.imgur.com/OekBjgM.gif)

---

## Задача: 
Написати бібліотеку, що дозволяє:
- Перетворення `HEX`            &rarr; `Little Endian`
- Перетворення `HEX`            &rarr; `Big Endian`
- Перетворення `Little Endian`  &rarr; `HEX`
- Перетворення `BIG Endian`     &rarr; `HEX`

## Test vectors:

### Vector #1:
| Value           |`ff00000000000000000000000000000000000000000000000000000000000000`                 |
|-----------------|-----------------------------------------------------------------------------------|
| Number of bytes |`32`                                                                               |
| Little-endian   |`255`                                                                              |
| Big-endian      |`115339776388732929035197660848497720713218148788040405586178452820382218977280`   |

---

### Vector #2:

| Value           |`aaaa000000000000000000000000000000000000000000000000000000000000`               |
|-----------------|---------------------------------------------------------------------------------|
| Number of bytes |`32`                                                                             |
| Little-endian   |`43690`                                                                          |
| Big-endian      |`77193548260167611359494267807458109956502771454495792280332974934474558013440`  |

---

### Vector #3:

| Value           |`FFFFFFFF`   |
|-----------------|-------------|
| Number of bytes |`4`          |
| Little-endian   |`4294967295` |
| Big-endian      |`4294967295` |

---

### Vector #4:

| Value           |`F000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000`   |
|-----------------|---------|
| Number of bytes |`512`    |
| Little-endian   |`240`    |
| Big-endian      |`979114576324830475023518166296835358668716483481922294110218890578706788723335115795775136189060210944584475044786808910613350098299181506809283832360654948074334665509728123444088990750984735919776315636114949587227798911935355699067813766573049953903257414411690972566828795693861196044813729172123152193769005290826676049325224028303369631812105737593272002471587527915367835952474124875982077070337970837392460768423348044782340688207323630599527945406427226264695390995320400314062984891593411332752703846859640346323687201762934524222363836094053204269986087043470117703336873406636573235808683444836432453459818599293667760149123595668832133083221407128310342064668595954073131257995767262426534143159642539179485013975461689493733866106312135829807129162654188209922755829012304582671671519678313609748646814745057724363462189490278183457296449014163077506949636570237334109910914728582640301294341605533983878368789071427913184794906223657920124153256147359625549743656058746335124502376663710766611046750739680547042183503568549468592703882095207981161012224965829605768300297615939788368703353944514111011011184191740295491255291545096680705534063721012625490368756140460791685877738232879406346334603566914069127957053440` |
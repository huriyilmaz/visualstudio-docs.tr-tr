---
title: Komut Penceresi
description: Doğrudan IDE'de Komut penceresi veya diğer adları yürütmek için Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- VS.CommandWindow
helpviewer_keywords:
- IDE, Command window
- Mark mode in Command window
- Command window
- Command mode in Command window
- IDE Command window
ms.assetid: 48711628-1909-4713-a73e-d7b714c77f8a
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: d6eac0c6ae6cd539f2a5dfc3b65d05482b2e282d
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126724928"
---
# <a name="command-window"></a>Komut Penceresi
Komut **penceresi,** komutları veya diğer adları doğrudan tümleşik geliştirme ortamında [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] (IDE) yürütmek için kullanılır. Hem menü komutlarını hem de hiçbir menüde görünmeen komutları yürütebilirsiniz. Komut penceresini **görüntülemek için** Görünüm **menüsünden Diğer Windows'ı** ve ardından Komut Penceresi'ne **tıklayın.** 

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin Değerlerini Görüntüleme
Bir değişkenin değerini kontrol etmek `varA` için Yazdırma [Komutu'na tıklayın:](../../ide/reference/print-command.md)

```cmd
>Debug.Print varA
```

Soru işareti (?) için bir diğer `Debug.Print` addır, bu nedenle bu komut da yazabilirsiniz:

```cmd
>? varA
```

Bu komutun her iki sürümü de değişkeninin değerini `varA` verir.

## <a name="entering-commands"></a>Komutları Girme
Büyüktür simgesi ( `>` ) yeni satır istemi olarak Komut penceresi kenarda görünür. Daha önce verilen komutlarda kaydırma yapmak için YUKARı OK ve AŞAĞI OK tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirme.|İfadenin başında soru işareti ( ) yer `?` alır.|`? myvar`|
|Hemen penceresine geçiş.|Pencereye `immed` büyüktür işareti olmadan girin (>)|`immed`|
|Hemen penceresinden Komut penceresi geri dönebilirsiniz.|Pencereye `cmd` girin.|`>cmd`|

Aşağıdaki kısayollar Komut modundayken gezinmenize yardımcı olur.

|Eylem|İmleç konumu|Keybinding|
|------------| - |----------------|
|Daha önce girilen komutlar listesinde döngüye girebilirsiniz.|Giriş satırı|YUKARı OK & OK|
|Pencereyi yukarı kaydırın.|Komut penceresi içeriği|CTRL+YUKARI OK|
|Pencereyi aşağı kaydırın.|Komut penceresi içeriği|AŞAĞI OK VEYA CTRL+AŞAĞI OK|

> [!TIP]
> Önceki komutun bir kısmını veya bir kısmını giriş satırına kaydırarak, bir kısmını veya hepsini vurgulayıp enter tuşuna basarak kopyaabilirsiniz.

## <a name="mark-mode"></a>İşaret Modu
Komut penceresinde önceki bir satıra **tıklarken** otomatik olarak İşaret moduna geçersiniz. Bu sayede herhangi bir metin düzenleyicisinde olduğu gibi önceki komutların metnini seçip düzenleyebilir ve kopyalayıp geçerli satıra yapıştırabilirsiniz.

## <a name="the-equals--sign"></a>Eşittir (=) İşareti
Komutu girmek için kullanılan pencere, eşittir işareti (=) ifadesinin karşılaştırma işleci veya atama işleci `EvaluateStatement` olarak yorumlanıp yorumlanamayacaklarını belirler.

Komut **penceresinde** eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. Komut penceresinde atama işleçlerini **kullanamazsınız.** Bu nedenle, örneğin, ve değişkenlerinin `varA` `varB` değerleri farklı ise, komut bir değeri `>Debug.EvaluateStatement(varA=varB)` `False` verir.

Hemen **penceresinde** ise eşittir işareti (=) atama işleci olarak yorumlanır. Bu nedenle, örneğin, `>Debug.EvaluateStatement(varA=varB)` komutu değişkeninin değerini `varA` değişkenine `varB` atar.

## <a name="parameters-switches-and-values"></a>Parametreler, Anahtarlar ve Değerler
Bazı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutlarda gerekli ve isteğe bağlı bağımsız değişkenler, anahtarlar ve değerler vardır. Bu tür komutlarla ilgilenmek için belirli kurallar uygulanır. Aşağıda terminolojiyi netleştirmek için zengin bir komutun bir örneği ve ardından yer vemektedir.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

Bu örnekte

- `Edit.ReplaceInFiles` komutu

- `/case` ve `/pattern:regex` anahtarlarıdır (eğik çizgi [/] karakteriyle başında)

- `regex` anahtarın `/pattern` değeridir; `/case` anahtarın değeri yoktur

- `var[1-3]+` ve `oldpar` parametredir

    > [!NOTE]
    > Boşluk içeren herhangi bir komut, parametre, anahtar veya değerin her iki tarafında da çift tırnak işareti olmalıdır.

Anahtarların ve parametrelerin konumu komut satırı üzerinde serbestçe değiştirilebilir; bunun yerine [Shell](../../ide/reference/shell-command.md) komutu özel olarak değiştirilebilir ve bu da anahtar ve parametrelerinin belirli bir sırada olması gerekir.

Bir komut tarafından desteklenen neredeyse her anahtarın iki biçimi vardır: kısa (bir karakter) form ve uzun bir form. Bir grupta birden çok kısa form anahtarı bir araya olabilir. Örneğin, `/p /g /m` alternatif olarak olarak ifade `/pgm` olabilir.

Kısa biçimli anahtarlar bir grup içinde birleştirildi ve bir değer verildi ise, bu değer her anahtar için geçerlidir. Örneğin, `/pgm:123` ile eşit `/p:123 /g:123 /m:123` olur. Gruptaki anahtarlardan herhangi biri bir değeri kabul etmiyorsa hata oluşur.

## <a name="escape-characters"></a>Kaçış Karakterleri
Komut satırı içinde bir caret (^) karakteri, onu takip eden karakterin denetim karakteri yerine tam anlamıyla yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerine düz tırnak işaretleri ("), boşluklar, baştaki eğik çizgi, çizgi işareti veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin,

```cmd
>Edit.Find ^^t /regex
```

İster tırnak içinde ister dışında olsun, bir işaret aynı şekilde işlev gösterir. Çizgideki son karakter bir karakterse yoksayılır. Burada gösterilen örnekte "^t" desenini arama gösterilmektedir.

## <a name="use-quotes-for-path-names-with-spaces"></a>Boşluklarla Yol Adları için Tırnak Kullanma
Örneğin, boşluk içeren bir yola sahip bir dosya açmak istiyorsanız, yol veya yol segmentinde boşluk içeren çift tırnaklar koymanız **gerekir: C: \\ "Program Files"** veya **"C:\Program Files"**.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio Komut](../../ide/reference/visual-studio-commands.md)

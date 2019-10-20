---
title: Komut Penceresi
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d89b06c406d0495a5699f707c85b4e9e9b3a804
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654584"
---
# <a name="command-window"></a>Komut Penceresi
**Komut** penceresi, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ORTAMıNDA (IDE) komutları veya diğer adları doğrudan yürütmek için kullanılır. Herhangi bir menüde görünmeyen menü komutlarını ve komutları çalıştırabilirsiniz. **Komut** penceresini görüntülemek Için, **Görünüm** menüsünde **diğer pencereler** ' i seçin ve **komut penceresi**' ni seçin.

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme
@No__t_0 değişkenin değerini denetlemek için [Print komutunu](../../ide/reference/print-command.md)kullanın:

```cmd
>Debug.Print varA
```

Soru işareti (?) `Debug.Print` için bir diğer addır, bu nedenle bu komut de yazılabilir:

```cmd
>? varA
```

Bu komutun her iki sürümü de `varA` değişkenin değerini döndürür.

## <a name="entering-commands"></a>Komutları girme
Büyüktür simgesi (`>`), yeni satırlar için istem olarak Komut penceresi sol kenarında görünür. Daha önce verilen komutlarda gezinmek için yukarı ok ve aşağı ok tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi bir soru işaretiyle (`?`) önyüz.|`? myvar`|
|Anında pencereye geçiş yapın.|Büyüktür işareti olmadan pencereye `immed` girin (>)|`immed`|
|Hemen bir pencereden Komut penceresi geri dönün.|Pencereye `cmd` girin.|`>cmd`|

Aşağıdaki kısayollar, komut modundayken gezinmenize yardımcı olur.

|Eylem|İmleç konumu|KeyBinding|
|------------| - |----------------|
|Daha önce girilen komutların listesi boyunca ilerleyin.|Giriş çizgisi|YUKARı ok & aşağı ok|
|Pencereyi yukarı kaydırın.|Komut penceresi içeriği|CTRL + YUKARı OK|
|Pencereyi aşağı kaydırın.|Komut penceresi içeriği|AŞAĞı ok veya CTRL + aşağı ok|

> [!TIP]
> Önceki bir komutun tümünü veya bir kısmını giriş satırına kaydırarak, bu bölümün tümünü veya bir kısmını vurgulayarak ENTER tuşuna basarak ekleyebilirsiniz.

## <a name="mark-mode"></a>İşaret modu
**Komut** penceresinde önceki herhangi bir satıra tıkladığınızda, işaret moduna otomatik olarak kaydırma yapabilirsiniz. Bu, herhangi bir metin düzenleyicisinde yaptığınız gibi önceki komutların metnini seçmenizi, düzenlemenizi ve kopyalamanızı sağlar ve bunları geçerli satıra yapıştırabilirsiniz.

## <a name="the-equals--sign"></a>Eşittir (=) Işareti
@No__t_0 komutunu girmek için kullanılan pencere, bir eşittir işareti (=) karşılaştırma işleci olarak mı yoksa atama işleci olarak mı yorumlanacağını belirler.

**Komut** penceresinde, bir eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. **Komut** penceresinde atama işleçlerini kullanamazsınız. Bu nedenle, örneğin, `varA` ve `varB` değişkenlerinin değerleri farklıysa, komut `>Debug.EvaluateStatement(varA=varB)` `False` değerini döndürür.

**Hemen** penceresinde, aksine, bir eşittir işareti (=) bir atama işleci olarak yorumlanır. Bu nedenle, örneğin, komut `>Debug.EvaluateStatement(varA=varB)` değişken `varB` değeri `varA` değişkenine atanır.

## <a name="parameters-switches-and-values"></a>Parametreler, anahtarlar ve değerler
Bazı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutlarında gerekli ve isteğe bağlı bağımsız değişkenler, anahtarlar ve değerler vardır. Belirli kurallar söz konusu komutlarla ilgilenirken geçerlidir. Aşağıda, terminolojiyi açıklığa kavuşturmak için zengin bir komuta bir örnek verilmiştir.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

Bu örnekte,

- `Edit.ReplaceInFiles` komuttur

- `/case` ve `/pattern:regex` anahtarlar (eğik çizgi [/] karakteriyle önceden ortaya çıkmış)

- `regex`, `/pattern` anahtarının değeridir; `/case` anahtarı bir değere sahip değil

- `var[1-3]+` ve `oldpar` parametreler

    > [!NOTE]
    > Boşluk içeren herhangi bir komutun, parametrenin, anahtarın veya değerin her iki tarafta da çift tırnak işareti olmalıdır.

Anahtar ve parametrelerin konumu, komut satırında, anahtar ve parametrelerini belirli bir sırada gerektiren [kabuk](../../ide/reference/shell-command.md) komutu hariç olmadan serbestçe değiştirilebilir.

Bir komutun desteklediği neredeyse her anahtarın iki formu vardır: kısa (bir karakter) form ve uzun bir form. Birden çok kısa formlu anahtar, bir grup içinde birleştirilebilir. Örneğin, `/p /g /m` alternatif olarak `/pgm` olarak ifade edilebilir.

Kısa biçimli anahtarlar bir grup içinde birleştirilirse ve bir değer verildiyse, bu değer her anahtar için geçerli olur. Örneğin, `/pgm:123` `/p:123 /g:123 /m:123` eşleledir. Gruptaki anahtarların herhangi biri bir değer kabul etmediğinde bir hata oluşur.

## <a name="escape-characters"></a>Kaçış karakterleri
Komut satırında bir şapka işareti (^) karakteri, bir denetim karakteri olarak değil, bundan hemen sonra gelen karakterin bir şekilde yorumlanması anlamına gelir. Bu, anahtar adları dışında bir parametre veya anahtar değerindeki düz tırnak işaretlerini ("), boşlukları, baştaki eğik çizgileri, yüzleri veya diğer sabit karakterleri eklemek için kullanılabilir. Örneğin,

```cmd
>Edit.Find ^^t /regex
```

Bir giriş işareti, tırnak işaretlerinin içinde mi yoksa dışında mı olduğunu görür. Şapka, satırdaki son karakter ise yok sayılır. Burada gösterilen örnekte, "^ t" deseninin nasıl aranacağı gösterilmektedir.

## <a name="use-quotes-for-path-names-with-spaces"></a>Boşluk içeren yol adları için tırnak Işaretleri kullanma
Örneğin, boşluk içeren bir yolu olan bir dosyayı açmak isterseniz, boşluk içeren yolun veya yol segmentinin çevresine çift tırnak koymanız gerekir: **C: \\ "Program Files"** veya **"C:\Program Files"** .

## <a name="see-also"></a>Ayrıca Bkz.

- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio Komutları](../../ide/reference/visual-studio-commands.md)
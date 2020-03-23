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
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cb855cbed67bffc5ff2fb63b1785c577dd9fea25
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570355"
---
# <a name="command-window"></a>Komut Penceresi
**Komut** penceresi, komutları veya diğer adları doğrudan [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] tümleşik geliştirme ortamında (IDE) yürütmek için kullanılır. Herhangi bir menüde görünmeyen hem menü komutlarını hem de komutları yürütebilirsiniz. **Komut** penceresini görüntülemek için **Görünüm** menüsünden **Diğer Windows'u** seçin ve **Komut Penceresi'ni**seçin.

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin Değerlerini Görüntüleme
Bir değişkenin `varA`değerini kontrol etmek [için, Yazdırma Komutu](../../ide/reference/print-command.md)kullanın:

```cmd
>Debug.Print varA
```

Soru işareti (?) için `Debug.Print`bir takma ad, bu komut da yazılabilir, böylece:

```cmd
>? varA
```

Bu komutun her iki sürümü de `varA`değişkenin değerini döndürecek.

## <a name="entering-commands"></a>Komutları Girme
Simgeden büyük`>`( ) komut penceresinin sol kenarında yeni satırlar için bir istek olarak görünür. Daha önce verilmiş komutlar arasında gezinmek için YUVARI OK ve DOWN ARROW tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi soru işaretiyle önsöz (`?`).|`? myvar`|
|Hemen penceresine geçin.|Pencereye işaretten büyük olmadan girin `immed` (>)|`immed`|
|Hemen penceresinden Komut penceresine geri dön.|Pencereye girin. `cmd`|`>cmd`|

Aşağıdaki kısayollar Komut modundayken gezinmenize yardımcı olur.

|Eylem|İmleç konumu|Keybinding|
|------------| - |----------------|
|Daha önce girilen komutlar listesinde geçiş yap.|Giriş satırı|YUKARı OK & Aşağı OK|
|Pencereyi yukarı kaydırın.|Komut penceresi içeriği|CTRL+YUKARI OK|
|Pencereyi aşağı kaydırın.|Komut penceresi içeriği|DOWN ARROW veya CTRL+DOWN OK|

> [!TIP]
> Önceki komutun tamamını veya bir kısmını giriş satırına kaydırarak, tamamını veya bir kısmını vurgulayarak ve enter tuşuna basarak kopyalayabilirsiniz.

## <a name="mark-mode"></a>İşaretle Modu
**Komut** penceresinde önceki herhangi bir satırı tıklattığınızda, otomatik olarak İşaretmoduna geçersiniz. Bu, önceki komutların metnini herhangi bir metin düzenleyicisinde olduğu gibi seçmenize, düzenleyeve kopyalamanıza ve bunları geçerli satıra yapıştırmaya olanak tanır.

## <a name="the-equals--sign"></a>Eşittir (=) İşaret
Komutu `EvaluateStatement` girmek için kullanılan pencere, eşit ler işaretinin (=) karşılaştırma işleci veya atama işleci olarak mı yorumlandığını belirler.

**Komut** penceresinde, eşitler işareti (=) karşılaştırma işleci olarak yorumlanır. **Komut** penceresinde atama işleçlerini kullanamazsınız. Yani, örneğin, `varA` değişkenlerin değerleri ve `varB` farklı ise, `>Debug.EvaluateStatement(varA=varB)` o zaman komutu bir değer döndürür `False`.

**Hemen** penceresinde, buna karşılık, eşitler işareti (=) bir atama işleci olarak yorumlanır. Yani, örneğin, komut `>Debug.EvaluateStatement(varA=varB)` değişkene `varA` değişkenin `varB`değerini atayacaktır.

## <a name="parameters-switches-and-values"></a>Parametreler, Anahtarlar ve Değerler
Bazı [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] komutlar gerekli ve isteğe bağlı bağımsız değişkenler, anahtarlar ve değerler var. Bu tür komutlarla uğraşırken belirli kurallar geçerlidir. Aşağıda terminolojiaçıklığa kavuşturmak için zengin bir komut bir örnektir.

```cmd
Edit.ReplaceInFiles /case /pattern:regex var[1-3]+ oldpar
```

Bu örnekte

- `Edit.ReplaceInFiles`komutudur

- `/case`ve `/pattern:regex` anahtarları (eğik çizgi [/] karakteri ile prefaced)

- `regex``/pattern` anahtarın değeridir; anahtarın `/case` değeri yoktur

- `var[1-3]+`ve `oldpar` parametreler

    > [!NOTE]
    > Boşlukları içeren herhangi bir komut, parametre, anahtar veya değer, her iki tarafta çift tırnak işaretleri olmalıdır.

Anahtarların ve parametrelerin konumu, belirli bir sırada anahtarlarını ve parametrelerini gerektiren [Shell](../../ide/reference/shell-command.md) komutu dışında komut satırında serbestçe değiştirilebilir.

Bir komut tarafından desteklenen hemen hemen her anahtarın iki biçimi vardır: kısa (bir karakter) form ve uzun bir form. Birden çok kısa form anahtarları bir grup halinde birleştirilebilir. Örneğin, `/p /g /m` dönüşümlü olarak `/pgm`ifade edilebilir.

Kısa form anahtarları bir grup halinde birleştirilir ve bir değer verilirse, bu değer her anahtar için geçerlidir. Örneğin, `/pgm:123` `/p:123 /g:123 /m:123`eşittir . Gruptaki anahtarlardan herhangi biri bir değeri kabul etmezse bir hata oluşur.

## <a name="escape-characters"></a>Kaçış Karakterleri
Komut satırındaki bir caret (^) karakter, onu hemen izleyen karakterin bir kontrol karakteri olarak değil, tam anlamıyla yorumlanması anlamına gelir. Bu, geçiş adları dışında, düz tırnak işaretleri ("), boşluklar, satır başları, bakımlar veya parametre veya anahtar değerindeki diğer tüm gerçek karakterleri katıştırmak için kullanılabilir. Örneğin,

```cmd
>Edit.Find ^^t /regex
```

Bir caret, tırnak işaretlerinin içinde veya dışında olsun aynı işlevi görür. Bir basamak satırdaki son karakterse, yoksayılır. Burada gösterilen örnek, "^t" deseninin nasıl arandığını göstermektedir.

## <a name="use-quotes-for-path-names-with-spaces"></a>Boşluklu Yol Adları için TırnakLar'ı Kullanma
Örneğin, boşluk içeren bir yol içeren bir dosyayı açmak istiyorsanız, boşluk içeren yol veya yol kesiminin etrafına çift tırnak eklemeniz gerekir: **C:\\"Program Dosyaları"** veya **"C:\Program Dosyaları"**.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Görsel Stüdyo Komutları](../../ide/reference/visual-studio-commands.md)

---
title: Komut Penceresi
ms.date: 02/25/2019
ms.topic: reference
dev_langs:
- VB
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b21cdb9136abe1e960e5b74bbf09e7d1694519d7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75568964"
---
# <a name="immediate-window"></a>Komut penceresi

İfadeleri ayıklamak ve değerlendirmek, deyimleri yürütmek ve değişken değerlerini yazdırmak için **Hemen** penceresini kullanın. **Hemen** penceresi, ifadeleri şu anda seçili projeyi oluşturarak ve kullanarak değerlendirir.

**Hemen** pencereyi görüntülemek için, düzenleme için bir proje açın ve ardından **Hata Ayıklama** > **Windows'u** **Windows** > Hemen seçin veya **Ctrl**+**Alt**+**I**tuşuna basın. **Debug.Immediate'ı** **Komut** penceresinde de girebilirsiniz.

**Hemen** penceresi IntelliSense'i destekler.

## <a name="display-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme

**Hemen** penceresi özellikle bir uygulamanın hata ayıklama özelliğinde kullanışlıdır. Örneğin, bir değişkenin `varA`değerini kontrol etmek için Yazdır [komutunu](../../ide/reference/print-command.md)kullanabilirsiniz:

```cmd
>Debug.Print varA
```

Soru işareti (?) için `Debug.Print`bir takma ad, bu komut da yazılabilir, böylece:

```cmd
? varA
```

Bu komutun her iki sürümü `varA`de değişkenin değerini döndürer.

> [!TIP]
> **Hemen** penceresinde bir Visual Studio komutu vermek için, komutu işaretten daha büyük (>) ile önsöze belirtmelisiniz. Birden çok komut girmek için [Komut penceresine](command-window.md)geçin.

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı ifade değerlendirmesi

Tasarım zamanında bir işlevi veya alt yordamı yürütmek için **Hemen** penceresini kullanabilirsiniz.

### <a name="execute-a-function-at-design-time"></a>Tasarım zamanında bir işlev yürütme

1. Aşağıdaki kodu Visual Basic konsol uygulamasına kopyalayın:

   ```vb
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. Hata **Ayıklama** menüsünde **Windows** > **Immediate'ı**seçin.

3. `?MyFunction(2)` **Hemen** penceresine yazın ve **Enter**tuşuna basın.

    **Hemen** penceresi `MyFunction` çalışır `4`ve görüntüler.

İşlev veya alt yordam bir kesme noktası içeriyorsa, Visual Studio yürütmeyi uygun noktada bozar. Daha sonra program durumunuzu incelemek için hata ayıklama pencerelerini kullanabilirsiniz. Daha fazla bilgi için [Walkthrough: Tasarım Zamanında Hata Ayıklama](../../debugger/walkthrough-debugging-at-design-time.md)bölümüne bakın.

Office projeleri, web projeleri, Akıllı Aygıt projeleri ve SQL projeleri için Visual Studio Araçları da dahil olmak üzere yürütme ortamının başlatılmasını gerektiren proje türlerinde tasarım zamanı ifade değerlendirmesini kullanamazsınız.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Çoklu proje çözümlerinde tasarım zamanı ifade değerlendirmesi

Tasarım zamanı ifade değerlendirmesi bağlamını oluştururken, Visual Studio Çözüm Gezgini'nde şu anda seçili projeye başvurur. Solution Explorer'da proje seçili değilse, Visual Studio işlevi başlangıç projesine göre değerlendirmeye çalışır. İşlev geçerli bağlamda değerlendirilemiyorsa, bir hata iletisi alırsınız. Çözüm için başlangıç projesi olmayan bir projedeki bir işlevi değerlendirmeye çalışıyorsanız ve bir hata alırsanız, Çözüm Gezgini'nde projeyi seçmeyi deneyin ve değerlendirmeyi yeniden deneyin.

## <a name="enter-commands"></a>Komutları girin

**Hemen** penceresinde Visual Studio komutları verirken büyük işareti (>) girin. Daha önce kullandığınız komutlarda gezinmek için **Yukarı ok** ve Aşağı **ok** tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi soru işareti (?) ile önsöz.|`? a+b`|
|Hemen modundayken geçici olarak Komut moduna girin (tek bir komutu yürütmek için).|Komutu girin, işaretten daha büyük (>) ile önyargılayın.|`>alias`|
|Komut penceresine geçin.|Pencereye girin, `cmd` işaretten daha büyük (>) ile önyüz.|`>cmd`|
|Hemen penceresine geri dön.|Pencereye işaretten büyük olmadan girin `immed` (>).|`immed`|

## <a name="mark-mode"></a>İşaret modu

**Hemen** penceresinde önceki herhangi bir satırı tıklattığınızda, otomatik olarak İşaretmoduna geçersiniz. Bu, önceki komutların metnini herhangi bir metin düzenleyicisinde olduğu gibi seçmenize, düzenleyeve kopyalamanıza ve bunları geçerli satıra yapıştırmaya olanak tanır.

## <a name="examples"></a>Örnekler

Aşağıdaki örnekte, bir Visual Basic projesi için **Hemen** penceresinde dört ifade ve bunların sonucu gösterilmektedir.

```cmd
j = 2
Expression has been evaluated and has no value

? j
2

j = DateTime.Now.Day
Expression has been evaluated and has no value

? j
26
```

## <a name="first-chance-exception-notifications"></a>İlk şans özel durum bildirimleri

Bazı ayarlar yapılandırmalarında, ilk şans özel durum bildirimleri **Hemen** penceresinde görüntülenir.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>Hemen penceresinde ilk şans özel durum bildirimlerini geçiş

1. **Görünüm** menüsünde **Diğer Windows'u**tıklatın ve **Çıktı'yı**tıklatın.

2. **Çıktı** penceresinin metin alanına sağ tıklayın ve ardından **Özel Durum İletileri'ni**seçin veya seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı ile Kodlarda gezinme](../../debugger/navigating-through-code-with-the-debugger.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
- [Walkthrough: Tasarım Zamanında Hata Ayıklama](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio'da Normal İfadeler Kullanma](../../ide/using-regular-expressions-in-visual-studio.md)

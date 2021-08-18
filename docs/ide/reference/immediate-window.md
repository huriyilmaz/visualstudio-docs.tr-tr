---
title: Komut Penceresi
description: İfadelerde hata ayıklamak ve ifadeleri değerlendirmek, deyimleri yürütmek ve değişken değerlerini yazdırmak için Anında penceresini kullanmayı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 84177dd5f6890e162c69de8ecbb883e5d933c028d39e13785575c97db8ec2ad5
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429218"
---
# <a name="immediate-window"></a>Komut penceresi

İfadelerde **hata** ayıklamak, ifadeleri değerlendirmek, deyimleri yürütmek ve değişken değerlerini yazdırmak için Hemen penceresini kullanın. Hemen **penceresi,** şu anda seçili olan projeyi kullanarak ve bu projeyi kullanarak ifadeleri değerlendirir.

Hemen penceresini görüntülemek **için,** düzenlemek için bir proje açın ve Ardından Anında Hata Ayıkla'Windows'yi  >    >  **seçin veya** **Ctrl** Alt I +  + **tuşlarına basın.** Komut penceresine **Debug.Immediate** de **girebilirsiniz.**

Anında **pencere** IntelliSense'i destekler.

## <a name="display-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme

Hemen **penceresi,** özellikle bir uygulamada hata ayıklarken kullanışlıdır. Örneğin değişkeninin değerini kontrol etmek için `varA` Yazdır komutunu [kullanabilirsiniz:](../../ide/reference/print-command.md)

```cmd
>Debug.Print varA
```

Soru işareti (?) için bir diğer `Debug.Print` addır, bu nedenle bu komut da yazabilirsiniz:

```cmd
? varA
```

Bu komutun her iki sürümü de değişkeninin değerini `varA` verir.

> [!TIP]
> Hemen penceresinde Visual Studio bir komut **yapmak** için komutun başında büyüktür işareti (>). Birden çok komut girmek için komutuna [Komut penceresi.](command-window.md)

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı ifadesi değerlendirmesi

Tasarım zamanında bir **işlev** veya alt yol yürütmek için Hemen penceresini kullanabilirsiniz.

### <a name="execute-a-function-at-design-time"></a>İşlevi tasarım zamanında yürütme

1. Aşağıdaki kodu bir konsol Visual Basic kopyalayın:

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

2. Hata **Ayıkla menüsünde** Hemen'i **Windows**  >  **seçin.**

3. Hemen `?MyFunction(2)` penceresine **yazın** ve Enter tuşuna **basın.**

    Hemen **penceresi** çalışır `MyFunction` ve `4` görüntülenir.

İşlev veya alt yol bir kesme noktası içeriyorsa, Visual Studio noktada yürütmeyi sonlar. Ardından hata ayıklayıcı pencerelerini kullanarak program durumuna bakabilirsiniz. Daha fazla bilgi için [bkz. Adım adım kılavuz: Tasarım Zamanında Hata Ayıklama.](../../debugger/walkthrough-debugging-at-design-time.md)

Tasarım zamanı ifadesi değerlendirmesini, Office için Visual Studio Araçları projeleri, web projeleri, Akıllı Cihaz projeleri ve SQL gibi yürütme ortamı başlatmayı gerektiren proje türlerinde SQL kullanabilirsiniz.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Çok projeli çözümlerde tasarım zamanı ifadesi değerlendirmesi

Tasarım zamanı ifadesi değerlendirmesi için bağlam kurulurken, Visual Studio içinde seçili olan projeye Çözüm Gezgini. Herhangi bir proje seçili Çözüm Gezgini, Visual Studio başlangıç projesine göre değerlendirmeye çalışır. İşlev geçerli bağlamda değerlendirilenene kadar bir hata iletisi alırsınız. Çözüm için başlangıç projesi değil bir proje içinde bir işlevi değerlendirmeye çalışıyorsanız ve bir hata alırsanız, Çözüm Gezgini projesini seçmeyi deneyin ve değerlendirmeyi yeniden deneyin.

## <a name="enter-commands"></a>Komutları girme

Hemen penceresinde komutlar > büyüktür (Visual Studio) **girin.** Daha önce **kullanılan komutlarda** **kaydırma yapmak** için Yukarı ok ve Aşağı ok tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirme.|İfadenin başında soru işareti (?).|`? a+b`|
|Anlık moddayken Komut modunu geçici olarak girin (tek bir komut yürütmek için).|Komutunu girin ve büyük bir işaretiyle önceden yazın (>).|`>alias`|
|Anahtara Komut penceresi.|Pencereye girin ve büyüktür işaretiyle önceden `cmd` >.|`>cmd`|
|Hemen penceresine geri dönebilirsiniz.|Pencereye `immed` büyüktür işareti olmadan girin (>).|`immed`|

## <a name="mark-mode"></a>İşaret modu

Anında penceresinde önceki satırlardan herhangi bir **satıra tıklarken** otomatik olarak İşaret moduna geçersiniz. Bu sayede herhangi bir metin düzenleyicisinde olduğu gibi önceki komutların metnini seçip düzenleyebilir ve kopyalayıp geçerli satıra yapıştırabilirsiniz.

## <a name="examples"></a>Örnekler

Aşağıdaki örnekte, bir proje için Anında penceresinde dört **ifade** ve bunların Visual Basic gösterilir.

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

## <a name="first-chance-exception-notifications"></a>birinci şans özel durum bildirimleri

Bazı ayar yapılandırmalarında, birinci şans özel durum bildirimleri Anında **penceresinde** görüntülenir.

### <a name="toggle-first-chance-exception-notifications-in-the-immediate-window"></a>İlk fırsat özel durum bildirimlerini Anında penceresinde açma/kapatın

1. Görünüm menüsünde **Diğer** **girişler'e ve Windows'a** **tıklayın.**

2. Çıkış penceresinin metin alanına sağ tıklayın **ve ardından** Özel Durum İletileri'ne tıklayın veya **seçimini kaldırın.**

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcısı ile Kodlarda gezinme](../../debugger/navigating-through-code-with-the-debugger.md)
- [Komut Penceresi](../../ide/reference/command-window.md)
- [Hata ayıklayıcıya ilk bakış](../../debugger/debugger-feature-tour.md)
- [Adım adım kılavuz: Tasarım Zamanında Hata Ayıklama](../../debugger/walkthrough-debugging-at-design-time.md)
- [Visual Studio Komut Diğer Adları](../../ide/reference/visual-studio-command-aliases.md)
- [Visual Studio'da Normal İfadeler Kullanma](../../ide/using-regular-expressions-in-visual-studio.md)

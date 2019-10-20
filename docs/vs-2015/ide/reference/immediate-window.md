---
title: Komut penceresi | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- VS.ImmediateWindow
helpviewer_keywords:
- design-time expression evaluation
- Immediate window
- first-chance exception notifications
ms.assetid: d33e7937-73f3-4c69-9df0-777a8713c6f2
caps.latest.revision: 28
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3177c92713f6fdeb9b9b8a47a0da38608714174d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72651276"
---
# <a name="immediate-window"></a>Komut Penceresi
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

**Komut** penceresi, ifadeleri hata ayıklamak ve değerlendirmek, deyimleri yürütmek, değişken değerlerini yazdırmak, vb. için kullanılır. Hata ayıklama sırasında geliştirme dili tarafından değerlendirilecek veya yürütülecek ifadeler girmenize olanak sağlar. **Hemen** penceresini göstermek için, bir projeyi düzenlemeniz için açın, ardından **Hata Ayıkla** menüsünde **Windows** ' u seçin ve **Hemen**' i seçin veya Ctrl + alt + ı tuşlarına basın.

 Bu pencereyi, bireysel [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komutları vermek için kullanabilirsiniz. Kullanılabilir komutlar, değişkenlere değer atamak için kullanılabilecek `EvaluateStatement` içerir. **Komut** penceresi de IntelliSense 'i destekler.

## <a name="displaying-the-values-of-variables"></a>Değişkenlerin değerlerini görüntüleme
 Bu pencere özellikle bir uygulamada hata ayıklarken yararlı olabilir. Örneğin, bir değişken `varA` değerini denetlemek için [Print komutunu](../../ide/reference/print-command.md)kullanabilirsiniz:

```
>Debug.Print varA
```

 Soru işareti (?) `Debug.Print` için bir diğer addır, bu nedenle bu komut de yazılabilir:

```
>? varA
```

 Bu komutun her iki sürümü de `varA` değişkenin değerini döndürür.

> [!NOTE]
> **Anında** pencerede bir [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] komutu vermek için, komutun işaretini büyüktür işareti (>) ile önceden başlatmalısınız. Birden çok komut girmek için, **komut** penceresine geçin.

## <a name="design-time-expression-evaluation"></a>Tasarım zamanı Ifade değerlendirmesi
 Tasarım zamanında bir işlevi veya alt yordamı yürütmek için **hemen** penceresini kullanabilirsiniz.

#### <a name="to-execute-a-function-at-design-time"></a>Tasarım zamanında bir işlevi yürütmek için

1. Aşağıdaki kodu bir [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] konsol uygulamasına kopyalayın:

   ```
   Module Module1

       Sub Main()
           MyFunction(5)
       End Sub

       Function MyFunction(ByVal input as Integer) As Integer
           Return input * 2
       End Function

   End Module
   ```

2. **Hata Ayıkla** menüsünde **Windows**' a ve ardından **hemen**' e tıklayın.

3. **Hemen** penceresine `?MyFunction(2)` yazın ve ENTER tuşuna basın.

    **Komut** penceresi `MyFunction` çalıştırır ve `4` görüntüler.

   İşlev veya alt yordam bir kesme noktası içeriyorsa [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)], uygun noktada yürütmeyi keser. Daha sonra program durumlarınızı incelemek için hata ayıklayıcı pencerelerini kullanabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: tasarım zamanında hata ayıklama](../../debugger/walkthrough-debugging-at-design-time.md).

   @No__t_0 projeler, Web projeleri, akıllı cihaz projeleri ve SQL projeleri de dahil olmak üzere bir yürütme ortamının başlatılması gereken proje türlerinde tasarım zamanı ifade değerlendirmesi kullanamazsınız.

### <a name="design-time-expression-evaluation-in-multi-project-solutions"></a>Çoklu proje çözümlerinde tasarım zamanı Ifade değerlendirmesi
 Tasarım zamanı ifade değerlendirmesi için bağlam oluştururken, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Çözüm Gezgini Şu anda seçili olan projeye başvurur. Çözüm Gezgini bir proje seçili değilse, [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] işlevi başlangıç projesine göre değerlendirmeye çalışır. İşlev geçerli bağlamda değerlendirilemez, bir hata iletisi alırsınız. Çözüm için başlangıç projesi olmayan bir projedeki bir işlevi değerlendirmeye çalışıyorsanız ve bir hata alırsanız, Çözüm Gezgini ' de projeyi seçip değerlendirmeyi yeniden deneyin.

## <a name="entering-commands"></a>Komutları girme
 **Komut penceresinde [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)]** komutlarını verirken, büyüktür işareti (>) girmelisiniz. Daha önce verilen komutlarda gezinmek için yukarı ok ve aşağı ok tuşlarını kullanın.

|Görev|Çözüm|Örnek|
|----------|--------------|-------------|
|Bir ifadeyi değerlendirin.|İfadeyi bir soru işaretiyle (?) önyüz.|`? a+b`|
|Komut modunu anında modda (tek bir komut yürütmek için) geçici olarak girin.|Komutu, işareti daha büyük (>) ile önceden girerek girin.|`>alias`|
|Komut penceresi geçin.|Pencereye daha büyük (>) işaretiyle `cmd` girin.|`>cmd`|
|Anında pencereye geri dönün.|@No__t_0, büyüktür işareti (>) olmadan pencereye girin.|`immed`|

## <a name="mark-mode"></a>İşaret modu
 **Hemen** penceredeki herhangi bir önceki satıra tıkladığınızda, işaret moduna otomatik olarak kaydırma yapabilirsiniz. Bu, herhangi bir metin düzenleyicisinde yaptığınız gibi önceki komutların metnini seçmenizi, düzenlemenizi ve kopyalamanızı sağlar ve bunları geçerli satıra yapıştırabilirsiniz.

## <a name="the-equals--sign"></a>Eşittir (=) Işareti
 @No__t_0 komutunu girmek için kullanılan pencere, bir eşittir işareti (=) karşılaştırma işleci olarak mı yoksa atama işleci olarak mı yorumlanacağını belirler.

 **Hemen** penceresinde bir eşittir işareti (=) atama işleci olarak yorumlanır. Bu nedenle, örneğin, komut

```
>Debug.EvaluateStatement(varA=varB)
```

 , değişken `varB` `varA` değişkenine atanır.

 **Komut** penceresinde, aksine, bir eşittir işareti (=) karşılaştırma işleci olarak yorumlanır. **Komut** penceresinde atama işlemlerini kullanamazsınız. Bu nedenle, örneğin, `varA` ve `varB` değişkenlerinin değerleri farklıysa, komut

```
>Debug.EvaluateStatement(varA=varB)
```

 `False` bir değer döndürür.

## <a name="first-chance-exception-notifications"></a>Birinci şans özel durum bildirimleri
 Bazı ayar yapılandırmalarında, ilk şans özel durum bildirimleri **komut** penceresinde görüntülenir.

#### <a name="to-toggle-first-chance-exception-notifications-in-the-immediate-window"></a>İlk şans özel durum bildirimlerini hemen pencerede değiştirmek için

1. **Görünüm** menüsünde **diğer pencereler**' e tıklayın ve **Çıkış**' a tıklayın.

2. **Çıkış** penceresinin metin alanına sağ tıklayın ve **özel durum iletileri**' ni seçin veya seçimini kaldırın.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual Studio hata ayıklayıcı [komut penceresi](../../ide/reference/command-window.md) hata ayıklaması [Ile kod aracılığıyla gezinme](../../debugger/navigating-through-code-with-the-debugger.md) [Visual Studio](../../debugger/debugging-in-visual-studio.md) [hata ayıklayıcısı temel kavramları](../../debugger/debugger-basics.md) [: tasarım zamanında](../../debugger/walkthrough-debugging-at-design-time.md) [Visual Studio komut diğer adları](../../ide/reference/visual-studio-command-aliases.md) düzenli olarak hata ayıklama [ Visual Studio 'da ifadeler](../../ide/using-regular-expressions-in-visual-studio.md)

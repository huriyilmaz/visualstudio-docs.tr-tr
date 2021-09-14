---
title: Visual Basic deyimlerini durdur | Microsoft Docs
description: Visual Studio bir kesme noktası ayarlamaya yönelik programsal bir alternatif sağlayan Visual Basic Stop ifadesini inceleyin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
- VB
helpviewer_keywords:
- End statements
- breakpoints, Stop statements
- debugging managed code, Stop statements vs breakpoints
- Stop statements, about Stop statements
- debugging [Visual Basic], Stop statements vs. breakpoints
ms.assetid: 4ad3fe5c-3dfb-4913-b2eb-a0b635751c18
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 624f7f586e9051edfee4d16d8706df22de64fda4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627860"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic'de durdur deyimleri

Visual Basic Stop deyimleri, kesme noktası ayarlamaya yönelik bir alternatif sağlar. Hata ayıklayıcı bir stop ifadesiyle karşılaştığında, programın yürütülmesini keser (kesme moduna girer). C# programcıları, öğesine yapılan bir çağrı kullanarak aynı etkiyi elde edebilir <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Bir stop ifadesini, kaynak kodunuzu düzenleyerek ayarlayabilir veya kaldırabilirsiniz. Bir kesme noktası gibi hata ayıklayıcı komutlarını kullanarak stop deyimlerini ayarlayamazsınız veya temizleyemezsiniz.

End ifadesinin aksine, stop deyimleri değişkenleri sıfırlamaz veya size tasarım moduna geri döndürmez. Uygulamayı çalıştırmaya devam etmek için hata ayıklama menüsünden devam ' ı seçebilirsiniz.

hata ayıklayıcı dışında bir Visual Basic uygulaması çalıştırdığınızda, Just-ın-Time hata ayıklaması etkinse Stop deyimleri hata ayıklayıcıyı başlatır. Just-In-Time hata ayıklaması etkinleştirilmemişse, stop deyimleri bir End deyimmiş gibi davranır ve yürütmeyi sonlandırır. queryunload veya Unload olayı gerçekleşmez, bu nedenle tüm Stop deyimlerini Visual Basic uygulamanızın yayın sürümünden kaldırmanız gerekir. Daha fazla bilgi için bkz. [tam zamanında hata ayıklama](just-in-time-debugging-in-visual-studio.md).

 Stop deyimlerini kaldırma zorunludur kaçınmak için, koşullu derleme kullanabilirsiniz:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Diğer bir seçenek de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> stop ifadesinin yerine bir ifade kullanmaktır. Bir <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> ifade yalnızca belirtilen koşul karşılanmazsa yürütmeyi keser. <xref:System.Diagnostics.Debug.Assert%2A> bir yayın sürümü oluşturduğunuzda deyimler otomatik olarak kaldırılır. Daha fazla bilgi için bkz. [Yönetilen koddaki Onaylamalar](assertions-in-managed-code.md). <xref:System.Diagnostics.Debug.Assert%2A>Her zaman hata ayıklama sürümünde yürütmeyi kesintiye neden olan bir bildirim istiyorsanız bunu yapabilirsiniz:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Ancak başka bir alternatif <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> yöntemi kullanmaktır:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hata ayıklayıcı güvenliği](debugger-security.md)
- [C#, F# ve Visual Basic Proje Türleri](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Yönetilen Kodda Hata Ayıklama](debugging-managed-code.md)

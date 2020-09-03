---
title: Visual Basic deyimlerini durdur | Microsoft Docs
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8f9ab4ef453a921371ab7ef4f272cd0e38f4108a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "71322530"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic'de durdur deyimleri

Visual Basic stop deyimleri, kesme noktası ayarlamaya yönelik bir alternatif sağlar. Hata ayıklayıcı bir stop ifadesiyle karşılaştığında, programın yürütülmesini keser (kesme moduna girer). C# programcıları, öğesine yapılan bir çağrı kullanarak aynı etkiyi elde edebilir <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> .

Bir stop ifadesini, kaynak kodunuzu düzenleyerek ayarlayabilir veya kaldırabilirsiniz. Bir kesme noktası gibi hata ayıklayıcı komutlarını kullanarak stop deyimlerini ayarlayamazsınız veya temizleyemezsiniz.

End ifadesinin aksine, stop deyimleri değişkenleri sıfırlamaz veya size tasarım moduna geri döndürmez. Uygulamayı çalıştırmaya devam etmek için hata ayıklama menüsünden devam ' ı seçebilirsiniz.

Hata ayıklayıcı dışında bir Visual Basic uygulaması çalıştırdığınızda, Just-In-Time hata ayıklaması etkinse stop deyimleri hata ayıklayıcıyı başlatır. Just-In-Time hata ayıklaması etkinleştirilmemişse, stop deyimleri bir End deyimmiş gibi davranır ve yürütmeyi sonlandırır. QueryUnload veya Unload olayı gerçekleşmez, bu nedenle tüm stop deyimlerini Visual Basic uygulamanızın yayın sürümünden kaldırmanız gerekir. Daha fazla bilgi için bkz. [tam zamanında hata ayıklama](just-in-time-debugging-in-visual-studio.md).

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

- [Hata Ayıklama Güvenliği](debugger-security.md)
- [C#, F# ve Visual Basic Proje Türleri](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Yönetilen Kodda Hata Ayıklama](debugging-managed-code.md)

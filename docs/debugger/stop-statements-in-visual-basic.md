---
title: Visual Basic |'de Stop Deyimleri Microsoft Docs
description: Bir Visual Basic noktası ayarlamaya program aracılığıyla alternatif sağlayan Visual Basic Stop deyimini Visual Studio.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122096901"
---
# <a name="stop-statements-in-visual-basic"></a>Visual Basic'de durdur deyimleri

Visual Basic Stop deyimi, kesme noktası ayarlamaya programlı bir alternatif sağlar. Hata ayıklayıcısı bir Stop deyimiyle karşılaştığında programın yürütülmesini durdurur (kesme moduna girer). C# programcıları çağrısı kullanarak aynı etkiyi elde ediyor <xref:System.Diagnostics.Debugger.Break%2A?displayProperty=nameWithType> olabilir.

Kaynak kodunuzu düzenleyerek Bir Stop deyimini ayarlayın veya kaldırın. Kesme noktası gibi hata ayıklayıcı komutlarını kullanarak Stop deyimlerini ayaramaz veya temizleyesiniz.

End deyiminden farklı olarak Stop deyimi değişkenleri sıfırlamaz veya sizi tasarım moduna geri dönmez. Uygulamayı çalıştırmaya devam etmek için Hata Ayıklama menüsünden Devam'ı seçebilirsiniz.

Hata ayıklayıcının Visual Basic bir uygulama çalıştırsanız, Tam Zamanında hata ayıklama etkinleştirilirse Bir Durdurma deyimi hata ayıklayıcıyı başlatıyor. Tam Zamanında hata ayıklama etkinleştirilmediyse Stop deyimi bir End deyimi gibi davranır ve yürütmeyi sonlandırılır. QueryUnload veya Unload olayı oluşmaz, bu nedenle tüm Stop deyimlerini uygulama uygulamanıza ilişkin Yayın sürümünden Visual Basic gerekir. Daha fazla bilgi için [bkz. Tam Zamanında Hata Ayıklama.](just-in-time-debugging-in-visual-studio.md)

 Stop deyimlerini kaldırma gereğini önlemek için koşullu derlemeyi kullanabilirsiniz:

```vb
#If DEBUG Then
   Stop
#Else
   ' Don't stop
#End If
```

Bir diğer alternatif de <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> Stop deyimi yerine deyimi kullanmak olabilir. Deyimi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType> yalnızca belirtilen bir koşul karşılanmazsa yürütmeyi sonlar. <xref:System.Diagnostics.Debug.Assert%2A> bir Yayın sürümü derleme sırasında deyimleri otomatik olarak kaldırılır. Daha fazla bilgi için [bkz. Yönetilen Kodda Onaylar.](assertions-in-managed-code.md) Hata Ayıklama sürümünde yürütmeyi her zaman bozan bir deyime sahip <xref:System.Diagnostics.Debug.Assert%2A> olmak için şunları yapabiliriz:

```csharp
Debug.Assert(false);
```

```vb
Debug.Assert(False)
```

Bir diğer alternatif de yöntemini kullanmak <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=nameWithType> olabilir:

```csharp
Debug.Fail("a clever output string goes here");
```

```vb
Debug.Fail("a clever output string goes here")
```

## <a name="see-also"></a>Ayrıca bkz.

- [Hata Ayıklayıcı Güvenliği](debugger-security.md)
- [C#, F# ve Visual Basic Proje Türleri](debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)
- [Yönetilen Kodda Hata Ayıklama](debugging-managed-code.md)

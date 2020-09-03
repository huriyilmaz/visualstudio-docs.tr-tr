---
title: 'CA1009: olay işleyicilerini doğru bildirin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1009
- DeclareEventHandlersCorrectly
helpviewer_keywords:
- CA1009
- DeclareEventHandlersCorrectly
ms.assetid: ab65c471-1449-49d2-9896-7b9af74284b4
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 6a4a4e2e6990772b50568043c4d18ff29248571d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85547894"
---
# <a name="ca1009-declare-event-handlers-correctly"></a>CA1009: Olay işleyicileri doğru olarak bildirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DeclareEventHandlersCorrectly|
|CheckId|CA1009|
|Kategori|Microsoft. Design|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir olayı işleyen bir temsilcinin doğru imza, dönüş türü veya parametre adı yoktur.

## <a name="rule-description"></a>Kural Tanımı
 Olay işleyicisi yöntemleri iki parametre alır. İlki türdür <xref:System.Object?displayProperty=fullName> ve ' sender ' olarak adlandırılmıştır. Bu olayda oluşan nesnedir. İkinci parametre türündedir <xref:System.EventArgs?displayProperty=fullName> ve ' e ' olarak adlandırılmıştır. Bu olay ile ilişkilendirilmiş olan verilerdir. Örneğin, bir dosya her açıldığında olay ortaya çıktığında, olay verileri genellikle dosyanın adını içerir.

 Olay işleyicisi yöntemleri bir değer döndürmemelidir. C# programlama dilinde, bu, dönüş türü tarafından belirtilir `void` . Bir olay işleyicisi, birden çok nesnede birden çok yöntemi çağırabilir. Yöntemlerin bir değer döndürmesine izin veriliyorsa, her olay için birden çok dönüş değeri oluşur ve yalnızca çağrılan son metodun değeri kullanılabilir olur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için, temsilcinin imzasını, dönüş türünü veya parametre adlarını düzeltin. Ayrıntılar için aşağıdaki örneğe bakın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, olayları işlemeye uygun bir temsilciyi gösterir. Bu olay işleyicisi tarafından çağrılabilen Yöntemler, tasarım yönergelerine göre belirtilen imzaya uyum sağlayabilir. `AlarmEventHandler` temsilcinin tür adıdır. `AlarmEventArgs` , olay verileri için temel sınıftan türetilir <xref:System.EventArgs> ve uyarı olay verilerini barındırır.

 [!code-cpp[FxCop.Design.EventsTwoParams#1](../snippets/cpp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cpp/FxCop.Design.EventsTwoParams.cpp#1)]
 [!code-csharp[FxCop.Design.EventsTwoParams#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/cs/FxCop.Design.EventsTwoParams.cs#1)]
 [!code-vb[FxCop.Design.EventsTwoParams#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Design.EventsTwoParams/vb/FxCop.Design.EventsTwoParams.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA2109: Görünen olay işleyicilerini gözden geçirin](../code-quality/ca2109-review-visible-event-handlers.md)

## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.EventArgs?displayProperty=fullName> <xref:System.Object?displayProperty=fullName>
 [NIB: olaylar ve temsilciler](https://msdn.microsoft.com/d98fd58b-fa4f-4598-8378-addf4355a115)

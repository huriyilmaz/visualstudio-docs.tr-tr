---
title: 'CA1412: ComSource Arabirimlerini IDispatch olarak Işaretle | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- MarkComSourceInterfacesAsIDispatch
- CA1412
helpviewer_keywords:
- CA1412
- MarkComSourceInterfacesAsIDispatch
ms.assetid: 131a7563-0410-443c-a8f5-52104250cfb4
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 86dc7042a48faa200ef9c360829b1756bc261ab0
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72652724"
---
# <a name="ca1412-mark-comsource-interfaces-as-idispatch"></a>CA1412: ComSource Arabirimlerini IDispatch olarak işaretleyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|MarkComSourceInterfacesAsIDispatch|
|CheckId|CA1412|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir tür <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> özniteliğiyle işaretlenir ve en az bir belirtilen arabirim, `InterfaceIsDispatch` değerine ayarlanmış <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> özniteliğiyle işaretlenmez.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>, bir sınıfın bileşen nesne modeli (COM) istemcilerine sunduğu olay arabirimlerini belirlemek için kullanılır. Visual Basic 6 COM istemcilerinin olay bildirimleri almasını sağlamak için bu arabirimlerin `InterfaceIsIDispatch` olarak sunulmalıdır. Varsayılan olarak, bir arabirim <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> özniteliğiyle işaretlenmemişse, Çift arabirim olarak sunulur.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Runtime.InteropServices.InterfaceTypeAttribute> özniteliğini ekleyin veya değiştirin. bu sayede değeri, <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute> özniteliğiyle belirtilen tüm arabirimler için ınterfaceisidispatch olarak ayarlanır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, arayüzlerden birinin kuralı ihlal ettiğini gösteren bir sınıfı gösterir.

 [!code-csharp[FxCop.Interoperability.MarkIDispatch#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/cs/FxCop.Interoperability.MarkIDispatch.cs#1)]
 [!code-vb[FxCop.Interoperability.MarkIDispatch#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.MarkIDispatch/vb/FxCop.Interoperability.MarkIDispatch.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1408: AutoDual ClassInterfaceType kullanma](../code-quality/ca1408-do-not-use-autodual-classinterfacetype.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: com havuzu tarafından Işlenen olayları](https://msdn.microsoft.com/7c9944b2-e951-4c3e-a0a1-59b2ae37d7fd) [, yönetilmeyen kodla birlikte çalışma](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)

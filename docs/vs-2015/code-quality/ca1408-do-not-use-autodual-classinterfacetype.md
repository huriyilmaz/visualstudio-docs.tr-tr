---
title: 'CA1408: oto Dual ClassInterfaceType kullanmayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotUseAutoDualClassInterfaceType
- CA1408
helpviewer_keywords:
- CA1408
- DoNotUseAutoDualClassInterfaceType
ms.assetid: 60ca5e02-3c51-42dd-942b-4f950eecfa0f
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b953a97d557e28cce50f554acc03797d4be38220
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534881"
---
# <a name="ca1408-do-not-use-autodual-classinterfacetype"></a>CA1408: AutoDual ClassInterFaceType kullanmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotUseAutoDualClassInterfaceType|
|CheckId|CA1408|
|Kategori|Microsoft. çalışabilirliği|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bileşen nesne modeli (COM) görünür türü <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliği değeri olarak ayarlanan özniteliğiyle işaretlenir `AutoDual` <xref:System.Runtime.InteropServices.ClassInterfaceType> .

## <a name="rule-description"></a>Kural Tanımı
 Çift arabirim kullanan türler, belirli bir arabirim düzenine bağlanmak için istemcileri etkinleştirir. Gelecek sürümdeki değişiklikler, türün düzeni veya bazı temel türler, arayüze bağlanan COM istemcilerini kesintiye uğratır. Varsayılan olarak, <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> öznitelik belirtilmemişse, yalnızca bir dağıtım arabirimi kullanılır.

 Aksi belirtilmedikçe genel olmayan genel türler COM 'a görünür; Tüm ortak ve genel türler COM 'da görünmez.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için <xref:System.Runtime.InteropServices.ClassInterfaceAttribute> özniteliğinin değerini `None` değerini değiştirin <xref:System.Runtime.InteropServices.ClassInterfaceType> ve arabirimi açık olarak tanımlayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Türün düzeninin ve temel türlerinin sonraki bir sürümde değişmemesini gerekmedikçe, bu kuraldan bir uyarıyı bastırmayın.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bir açık arabirim kullanmak için kuralı ve bir yeniden bildirimini ihlal eden bir sınıfı gösterir.

 [!code-csharp[FxCop.Interoperability.AutoDual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/cs/FxCop.Interoperability.AutoDual.cs#1)]
 [!code-vb[FxCop.Interoperability.AutoDual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Interoperability.AutoDual/vb/FxCop.Interoperability.AutoDual.vb#1)]

## <a name="related-rules"></a>İlgili kurallar
 [CA1403: Otomatik yerleşim türleri COM görünebilir olmamalıdır](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)

 [CA1412: ComSource arabirimlerini IDispatch olarak işaretleyin](../code-quality/ca1412-mark-comsource-interfaces-as-idispatch.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Yönetilmeyen kod ile](https://msdn.microsoft.com/library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258) birlikte çalışabilirlik Için [sınıf arabirimi](https://msdn.microsoft.com/733c0dd2-12e5-46e6-8de1-39d5b25df024) [niteleyen .NET türlerini](https://msdn.microsoft.com/library/4b8afb52-fb8d-4e65-b47c-fd82956a3cdd) tanıtma

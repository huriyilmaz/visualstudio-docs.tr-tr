---
title: 'CA2102: CLSCompliant olmayan özel durumları genel işleyicilerde yakala | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2102
- CatchNonClsCompliantExceptionsInGeneralHandlers
helpviewer_keywords:
- CA2102
ms.assetid: bf2df68f-d386-4379-ad9e-930a2c2e930d
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e2335b6d2bc3a5e99f0e6de1afefac4f42de0501
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85521309"
---
# <a name="ca2102-catch-non-clscompliant-exceptions-in-general-handlers"></a>CA2102: CLSCompliant olmayan özel durumları genel işleyiciler içinde yakalayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|CatchNonClsCompliantExceptionsInGeneralHandlers|
|CheckId|CA2102|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ya da ile işaretlenmemiş bir derlemedeki üye, <xref:System.Runtime.CompilerServices.RuntimeCompatibilityAttribute> `RuntimeCompatibility(WrapNonExceptionThrows = false)` <xref:System.Exception?displayProperty=fullName> hemen aşağıdaki genel catch bloğunu işleyen ve içermeyen bir catch bloğu içerir. Bu kural [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derlemeleri yoksayar.

## <a name="rule-description"></a>Kural Tanımı
 <xref:System.Exception>Tüm ortak dil belirtimi (CLS) uyumlu özel durumlarını yakalayan bir catch bloğu. Ancak, CLS uyumlu olmayan özel durumları yakalamaz. CLS uyumlu olmayan özel durumlar yerel koddan veya Microsoft ara dili (MSIL) derleyicisi tarafından oluşturulan yönetilen koddan oluşturulabilir. C# ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] derleyicilerin CLS uyumlu olmayan özel durumların atılamayacağını ve [!INCLUDE[vbprvb](../includes/vbprvb-md.md)] CLS uyumlu olmayan özel durumları yakalamayacağını unutmayın. Catch bloğunun amacı tüm özel durumları işlemek ise, aşağıdaki genel catch bloğu sözdizimini kullanın.

- Þ `catch {}`

- C++: `catch(...) {}` veya `catch(Object^) {}`

  İşlenmemiş CLS uyumlu olmayan bir özel durum, önceden izin verilen izinler catch bloğunda kaldırıldığında bir güvenlik sorunu haline gelir. CLS uyumlu olmayan özel durumlar yakalanmadığı için, CLS uyumlu olmayan bir özel durum oluşturan kötü niyetli bir yöntem yükseltilmiş izinlerle çalıştırılabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Amaç tüm özel durumları yakalamada, genel bir catch bloğu yerine koymak veya eklemek ya da derlemeyi işaretlemek için bu kural ihlalini onarmak için `RuntimeCompatibility(WrapNonExceptionThrows = true)` . İzinler catch bloğunda kaldırılırsa, genel catch bloğundaki işlevselliği çoğaltın. Tüm özel durumları işleme amacı değilse, <xref:System.Exception> özel özel durum türlerini işleyen catch bloklarıyla işleyen catch bloğunu değiştirin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Try bloğu CLS uyumlu olmayan bir özel durum oluşturabilen deyimler içermiyorsa, bu kuraldan bir uyarıyı gizlemek güvenlidir. Herhangi bir yerel veya yönetilen kod CLS uyumlu olmayan bir özel durum oluşturabileceğinden, bu, try bloğu içindeki tüm kod yollarında yürütülebilecek tüm kodlar için bilgi gerektirir. CLS uyumlu olmayan özel durumların ortak dil çalışma zamanı tarafından oluşturulduğuna dikkat edin.

## <a name="example"></a>Örnek
 Aşağıdaki örnekte, CLS uyumlu olmayan bir özel durum oluşturan bir MSIL sınıfı gösterilmektedir.

```
.assembly ThrowNonClsCompliantException {}
.class public auto ansi beforefieldinit ThrowsExceptions
{
   .method public hidebysig static void
         ThrowNonClsException() cil managed
   {
      .maxstack  1
      IL_0000:  newobj     instance void [mscorlib]System.Object::.ctor()
      IL_0005:  throw
   }
}
```

## <a name="example"></a>Örnek
 Aşağıdaki örnek, kuralını karşılayan genel bir catch bloğunu içeren bir yöntemi gösterir.

 [!code-csharp[FxCop.Security.CatchNonClsCompliantException#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.CatchNonClsCompliantException/cs/FxCop.Security.CatchNonClsCompliantException.cs#1)]

 Önceki örnekleri aşağıdaki şekilde derleyin.

```
ilasm /dll ThrowNonClsCompliantException.il
csc /r:ThrowNonClsCompliantException.dll CatchNonClsCompliantException.cs
```

## <a name="related-rules"></a>İlgili kurallar
 [CA1031: Genel özel durum türlerini yakalamayın](../code-quality/ca1031-do-not-catch-general-exception-types.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Özel durumlar ve özel durum işleme](https://msdn.microsoft.com/library/0001887f-4fa2-47e2-8034-2819477e2344) [Ilasm.exe (Il Assembler)](https://msdn.microsoft.com/library/4ca3a4f0-4400-47ce-8936-8e219961c76f) [güvenlik denetimlerini geçersiz kılma](https://msdn.microsoft.com/4acdeff5-fc05-41bf-8505-7387cdbfca28) [Dil bağımsızlığı ve dilden bağımsız bileşenler](https://msdn.microsoft.com/library/4f0b77d0-4844-464f-af73-6e06bedeafc6)

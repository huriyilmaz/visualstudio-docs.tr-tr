---
title: 'CA2132: varsayılan oluşturucular en az temel tür varsayılan oluşturucular kadar kritik olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2132
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 0ae271b116b372d4ae732d97ff3f9651ff9db426
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643295"
---
# <a name="ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors"></a>CA2132: Varsayılan oluşturucular en az taban tür varsayılan oluşturucular kadar kritik olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|Defaultconstructorsmusthavepotenttransparency|
|CheckId|CA2132|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

> [!NOTE]
> Bu uyarı yalnızca CoreCLR (CLR 'nin Silverlight Web uygulamalarına özgü sürümü) çalıştıran koda uygulanır.

## <a name="cause"></a>Sebep
 Türetilmiş bir sınıfın varsayılan oluşturucusunun saydamlık özniteliği, temel sınıfın saydamlığı kadar kritik değildir.

## <a name="rule-description"></a>Kural Tanımı
 @No__t_0 olan türler ve Üyeler Silverlight uygulama kodu tarafından kullanılamaz. Kritik güvenlik türleri ve üyeleri, yalnızca Silverlight sınıf kütüphanesi için .NET Framework'ündeki güvenilen kod tarafından kullanılabilir. Türetilmiş sınıftaki ortak veya korumalı oluşturma, onun temel sınıfından aynı düzeyde veya daha saydam olması gerektiğinden uygulama içindeki sınıf SecurityCritical olarak işaretlenmiş bir sınıftan türeyemez.

 CoreCLR platform kodu için, bir temel türün ortak veya korumalı olmayan bir varsayılan Oluşturucusu varsa, türetilen tür varsayılan Oluşturucu devralma kurallarına uymalıdır. Türetilmiş türün aynı zamanda varsayılan bir oluşturucusu olmalıdır ve bu Oluşturucu en az temel türün kritik varsayılan oluşturucu olarak olmalıdır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 İhlalin giderilmesi için, türü kaldırın veya güvenlik açısından saydam olmayan türden türemeyin.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan gelen uyarıları göstermez. Bu kuralın uygulama kodu tarafından ihlal edilmesine yol açacaktır ve bir <xref:System.TypeLoadException> ile birlikte yüklemeyi reddediyor.

### <a name="code"></a>Kod
 [!code-csharp[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../snippets/csharp/VS_Snippets_CodeAnalysis/fxcop.security.ca2132.defaultconstructorsmusthaveconsistenttransparency/cs/ca2132 - defaultconstructorsmusthaveconsistenttransparency.cs#1)]

### <a name="comments"></a>Açıklamalar

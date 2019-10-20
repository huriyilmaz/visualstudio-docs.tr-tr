---
title: 'CA2122: bağlantı taleplerine dolaylı olarak yöntemleri gösterme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2122
- DoNotIndirectlyExposeMethodsWithLinkDemands
helpviewer_keywords:
- DoNotIndirectlyExposeMethodsWithLinkDemands
- CA2122
ms.assetid: 3eda58e7-c6ec-41c3-8112-ae0841109c6a
caps.latest.revision: 19
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 099e5f3f9a09eef57ce1b888601f61e85ceb97c5
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72643399"
---
# <a name="ca2122-do-not-indirectly-expose-methods-with-link-demands"></a>CA2122: Bağlantı talepleri olan yöntemleri dolaylı olarak açığa çıkarmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotIndirectlyExposeMethodsWithLinkDemands|
|CheckId|CA2122|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Ortak veya korumalı bir üyenin [bağlantı talepleri](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) vardır ve herhangi bir güvenlik denetimi gerçekleştirmediğinden bir üye tarafından çağırılır.

## <a name="rule-description"></a>Kural Tanımı
 Bağlantı talebi, yalnızca o anki çağırıcı izinlerini denetler. Bir üye `X` çağıranların güvenlik taleplerini yoksa ve bir bağlantı talebi tarafından korunan kodu çağırırsa, gerekli izne sahip olmayan bir çağıran, korumalı üyeye erişmek için `X` kullanabilir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bir güvenlik [verileri ekleyin ve](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) isteğe bağlı olarak, bağlantıya talep korumalı üyeye güvenli olmayan erişim sağlamaz.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı güvenle bastırmak için, kodunuzun çağıranlar için bir bozucu şekilde kullanılabilecek işlemlere veya kaynaklara erişimini vermediğinden emin olmanız gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örneklerde, kuralı ihlal eden bir kitaplık ve kitaplığın zayıflılığını gösteren bir uygulama gösterilmektedir. Örnek kitaplık, birlikte kuralı ihlal eden iki yöntem sağlar. @No__t_0 yöntemi, ortam değişkenlerine sınırsız erişim talebi ile korunmuş olur. @No__t_0 yöntemi, arayanlara `EnvironmentSetting` çağırmadan önce hiçbir güvenlik talebi yapmaz.

 [!code-csharp[FxCop.Security.UnsecuredDoNotCall#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.UnsecuredDoNotCall/cs/FxCop.Security.UnsecuredDoNotCall.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, güvenli olmayan kitaplık üyesini çağırır.

 [!code-csharp[FxCop.Security.TestUnsecuredDoNot1#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestUnsecuredDoNot1/cs/FxCop.Security.TestUnsecuredDoNot1.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Güvenli olmayan üyenin değeri: seattle.corp.contoso.com**
## <a name="see-also"></a>Ayrıca Bkz.
 [Güvenli kodlama yönergeleri](https://msdn.microsoft.com/library/4f882d94-262b-4494-b0a6-ba9ba1f5f177) [bağlantı talep](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6)

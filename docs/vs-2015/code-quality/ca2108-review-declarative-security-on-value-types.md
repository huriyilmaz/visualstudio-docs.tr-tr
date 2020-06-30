---
title: 'CA2108: değer türlerinde bildirime dayalı güvenliği gözden geçirin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
helpviewer_keywords:
- ReviewDeclarativeSecurityOnValueTypes
- CA2108
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 03918353b66c36698b5d17b332da052b6d95c87a
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85544397"
---
# <a name="ca2108-review-declarative-security-on-value-types"></a>CA2108: Değer türleri üzerinde bildirimsel güvenliği gözden geçirin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|ReviewDeclarativeSecurityOnValueTypes|
|CheckId|CA2108|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Ortak veya korumalı bir değer türü, bir [veri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) veya [bağlantı taleplerine](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d)karşı korunur.

## <a name="rule-description"></a>Kural Tanımı
 Değer türleri, diğer oluşturucular yürütmeden önce varsayılan oluşturucularında ayrılır ve başlatılır. Bir değer türü talep veya LinkDemand tarafından güvenli hale getirilmezse ve çağıranın güvenlik denetimini karşılayan izinleri yoksa, varsayılan dışında bir Oluşturucu başarısız olur ve bir güvenlik özel durumu oluşturulur. Değer türü serbest bırakılmıyor; Bu, varsayılan oluşturucusu tarafından ayarlanmış durumda bırakılır. Değer türünün bir örneğini geçiren bir çağıranın örnek oluşturma veya örneğe erişme iznine sahip olduğunu varsayın.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Türden güvenlik denetimini kaldırmadığınız ve kendi yerinde Yöntem düzeyi güvenlik denetimlerini kullanmadığınız müddetçe, bu kural ihlaline çözüm yükleyemezsiniz. İhlalin bu şekilde düzeltildiğine, yetersiz izinlere sahip çağıranların değer türünün örneklerini almasını engellemez. Değer türünün bir örneğinin varsayılan durumunda, hassas bilgileri kullanıma sunmadığından ve zararlı bir şekilde kullanılamayacak olduğundan emin olmanız gerekir.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Herhangi bir çağıran, güvenlik tehdidi oluşturmadan bu kuraldan bir uyarıyı, varsayılan durumunda değer türünün örneklerini elde edebilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden bir değer türü içeren bir kitaplığı göstermektedir. `StructureManager`Türün, değer türünün bir örneğini geçiren bir çağıranın örnek oluşturma veya bu örneğe erişme iznine sahip olduğunu varsaydığını unutmayın.

 [!code-csharp[FxCop.Security.DemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.DemandOnValueType/cs/FxCop.Security.DemandOnValueType.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki uygulama, kitaplığın zayıflılığını gösterir.

 [!code-csharp[FxCop.Security.TestDemandOnValueType#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestDemandOnValueType/cs/FxCop.Security.TestDemandOnValueType.cs#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Yapı özel Oluşturucusu: istek başarısız oldu.** 
 **Yeni değerler SecuredTypeStructure 100 100** 
 **Yeni değerler SecuredTypeStructure 200 200**
## <a name="see-also"></a>Ayrıca Bkz.
 [Talep](https://msdn.microsoft.com/library/a33fd5f9-2de9-4653-a4f0-d9df25082c4d) [verileri ve modelleme](https://msdn.microsoft.com/library/8c37635d-e2c1-4b64-a258-61d9e87405e6) bağlantısı

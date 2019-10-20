---
title: 'CA2219: özel durum yan tümcelerinde özel durum yükseltmeyin | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
helpviewer_keywords:
- DoNotRaiseExceptionsInExceptionClauses
- CA2219
ms.assetid: 7b9b0bee-4e8e-49a4-8c40-52142b49061f
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: ebce51d360518d1cc66f652714c59d27751586b2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668874"
---
# <a name="ca2219-do-not-raise-exceptions-in-exception-clauses"></a>CA2219: Özel durum yan tümceleri içinde özel durum harekete geçirmeyin
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotRaiseExceptionsInExceptionClauses|
|CheckId|CA2219|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Bölünmez, kırılmamış|

## <a name="cause"></a>Sebep
 Bir `finally`, filtre veya hata tümceciğinden bir özel durum atılır.

## <a name="rule-description"></a>Kural Tanımı
 Özel durum yan tümcesinde bir özel durum ortaya çıktığında hata ayıklama zorluğunu büyük ölçüde artırır.

 Bir `finally` veya hata yan tümcesinde bir özel durum ortaya çıktığında, yeni özel durum varsa etkin özel durumu gizler. Bu, özgün hatayı algılamaya ve hata ayıklamasına keskin hale getirir.

 Bir filtre yan tümcesinde bir özel durum harekete geçirilir, çalışma zamanı özel durumu sessizce yakalar ve filtrenin false olarak değerlendirilmesini sağlar. Filtre ve bir filtreden throw bir özel durum arasındaki farkı anlatmak için bir yol yoktur. Bu, filtrenin mantığındaki hataları algılamayı ve hata ayıklamayı zorlaştırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için `finally`, filtre veya hata yan tümcesinden açık bir özel durum kullanmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kural için bir uyarı bastırmayın. Bir özel durum yan tümcesinde oluşturulan özel durumun, yürütülen koda bir avantaj sağladığı bir senaryo yoktur.

## <a name="related-rules"></a>İlgili kurallar
 [CA1065: Beklenmedik konumlarda özel durumlar tetiklemeyin](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Tasarım Uyarıları](../code-quality/design-warnings.md)

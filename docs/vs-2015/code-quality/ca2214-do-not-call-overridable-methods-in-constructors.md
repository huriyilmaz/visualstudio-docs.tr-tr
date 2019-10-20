---
title: 'CA2214: oluşturucularda geçersiz kılınabilir yöntemleri çağırmayın | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- DoNotCallOverridableMethodsInConstructors
- CA2214
helpviewer_keywords:
- CA2214
- DoNotCallOverridableMethodsInConstructors
ms.assetid: 335b57ca-a6e8-41b4-a20e-57ee172c97c3
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 78702298bab484a95bb8108150415ec0b31ede7d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72662906"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Geçersiz kılınabilir yöntemleri oluşturucular içinde çağırmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Korumasız bir türün Oluşturucusu sınıfında tanımlanmış sanal bir yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Bir sanal yöntem çağrıldığında, yöntemi yürüten gerçek tür çalışma zamanına kadar seçili değildir. Bir Oluşturucu sanal bir yöntemi çağırdığında, yöntemi çağıran örnek için olan oluşturucunun yürütülmemiş olması mümkündür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, türün oluşturucularının içinden bir türün sanal yöntemlerini çağırmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Sanal yöntem çağrısını ortadan kaldırmak için oluşturucunun yeniden tasarlanması gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden etkisini gösterir. Test uygulaması, temel sınıfının (`BadlyConstructedType`) oluşturucusunun yürütülmesine neden olan `DerivedType` örneğini oluşturur. `BadlyConstructedType` ' ın Oluşturucusu, `DoSomething` sanal metodunu yanlış çağırır. Çıktının gösterdiği gibi, `DerivedType.DoSomething()` yürütülür ve `DerivedType` oluşturucusunun yürütmeden önce bunu yapar.

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Temel ctor çağrılıyor.** 
**türetilen Dosometem çağrıldı, başlatıldı mı? ** **Türetilmiş ctor çağrısı 
.**

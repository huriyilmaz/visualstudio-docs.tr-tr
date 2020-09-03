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
ms.openlocfilehash: ad467e880b3281a75db2627108af0e0b2f90ea99
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85534465"
---
# <a name="ca2214-do-not-call-overridable-methods-in-constructors"></a>CA2214: Geçersiz kılınabilir metotları oluşturucular içinde çağırmayın
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|DoNotCallOverridableMethodsInConstructors|
|CheckId|CA2214|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Korumasız bir türün Oluşturucusu sınıfında tanımlanmış sanal bir yöntemi çağırır.

## <a name="rule-description"></a>Kural Tanımı
 Bir sanal yöntem çağrıldığında, yöntemi yürüten gerçek tür çalışma zamanına kadar seçili değildir. Bir Oluşturucu sanal bir yöntemi çağırdığında, yöntemi çağıran örnek için olan oluşturucunun yürütülmemiş olması mümkündür.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kuralın ihlalini onarmak için, türün oluşturucularının içinden bir türün sanal yöntemlerini çağırmayın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Sanal yöntem çağrısını ortadan kaldırmak için oluşturucunun yeniden tasarlanması gerekir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, bu kuralı ihlal eden etkisini gösterir. Test uygulaması `DerivedType` , kendi temel sınıf () oluşturucusunun yürütülmesine neden olan bir örneği oluşturur `BadlyConstructedType` . `BadlyConstructedType`oluşturucusunun sanal yöntemi yanlış bir şekilde çağırır `DoSomething` . Çıktının gösterdiği gibi,, `DerivedType.DoSomething()` yürütülür, ve kurucu yürütmeden önce bunu yapar `DerivedType` .

 [!code-csharp[FxCop.Usage.CtorVirtual#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/cs/FxCop.Usage.CtorVirtual.cs#1)]
 [!code-vb[FxCop.Usage.CtorVirtual#1](../snippets/visualbasic/VS_Snippets_CodeAnalysis/FxCop.Usage.CtorVirtual/vb/FxCop.Usage.CtorVirtual.vb#1)]

 Bu örnek aşağıdaki çıktıyı üretir.

 **Temel ctor çağrılıyor.** 
 **Türetilmiş Dosometem çağrıldı, başlatıldı mı? ** 
 **Türetilmiş bir ctor çağrısı yok.**

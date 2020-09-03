---
title: 'CA2226: operatörler simetrik aşırı yüklemeleri içermelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
helpviewer_keywords:
- OperatorsShouldHaveSymmetricalOverloads
- CA2226
ms.assetid: d202401a-ea14-4559-b15e-0ea4f5b68789
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 430a8d3cfd3b8ced45b60bd9dc70211711886d43
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85540575"
---
# <a name="ca2226-operators-should-have-symmetrical-overloads"></a>CA2226: İşleçler simetrik aşırı yüklemelere sahip olmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|OperatorsShouldHaveSymmetricalOverloads|
|CheckId|CA2226|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Nedeni
 Bir tür, eşitlik ya da eşitsizlik operatörünü uygular ve ters işleci uygulamaz.

## <a name="rule-description"></a>Kural Tanımı
 Eşitlik veya eşitsizlik bir tür örneklerine uygulanabilir olduğu ve ters işleç tanımsız olduğu durumlar yoktur. Türler, genellikle eşitlik işlecinin negated Value değerini döndürerek eşitsizlik işlecini uygular.

 C# derleyicisi, bu kuralın ihlalleri için bir hata verir.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini onarmak için hem eşitlik hem de eşitsizlik işleçlerini uygulayın veya var olan birini kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Türü ile tutarlı bir şekilde çalışmaz [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] .

## <a name="related-rules"></a>İlgili kurallar
 [CA1046: Eşittir işlecini başvuru türlerinde aşırı yüklemeyin](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)

 [CA2225: İşleç aşırı yüklemeleri adlandırılmış alternatiflere sahiptir](../code-quality/ca2225-operator-overloads-have-named-alternates.md)

 [CA2224: Eşittir işlecini aşırı yüklerken Equals'ı geçersiz kılın](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)

 [CA2218: GetHashCode'u Eşittir'i geçersiz kılarak geçersiz kılın](../code-quality/ca2218-override-gethashcode-on-overriding-equals.md)

 [CA2231: Eşittir işlecini ValueType.Equals'ı geçersiz kılarak aşırı yükleyin](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)

---
title: 'CA1722: tanımlayıcılardan önek yanlış olmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotHaveIncorrectPrefix
- CA1722
helpviewer_keywords:
- CA1722
- IdentifiersShouldNotHaveIncorrectPrefix
ms.assetid: c3313c51-d004-4f9a-a0d1-6c4c4a1fb1e6
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: a7f4f932f8e2db9a558d7440d8965ce5924043b8
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544488"
---
# <a name="ca1722-identifiers-should-not-have-incorrect-prefix"></a>CA1722: Tanımlayıcılar yanlış ön ek içermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|IdentifiersShouldNotHaveIncorrectPrefix|
|CheckId|CA1722|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Tanımlayıcının ön eki yanlış.

## <a name="rule-description"></a>Kural Tanımı
 Kural gereği, programlama öğelerinin belirli bir önek ile başlayan adları vardır.

 Tür adlarında belirli bir önek yoktur ve ' C ' öneki eklenmelidir. Bu kural, ' CMyClass ' gibi tür adları için ihlalleri raporlar ve ' cache ' gibi tür adları için ihlalleri rapor etmez.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Öneki tanımlayıcıdan kaldırın.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="related-rules"></a>İlgili kurallar
 [CA1715: Tanımlayıcılar doğru ön eke sahip olmalıdır](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)

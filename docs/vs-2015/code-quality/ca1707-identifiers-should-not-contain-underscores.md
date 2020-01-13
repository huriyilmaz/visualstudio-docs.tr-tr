---
title: 'CA1707: tanımlayıcılar alt çizgi içermemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- IdentifiersShouldNotContainUnderscores
- CA1707
helpviewer_keywords:
- CA1707
- IdentifiersShouldNotContainUnderscores
ms.assetid: 5fb539ef-c304-4323-90c0-b14386da9774
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 5a06e87f8d28ceb225e240d7702a47e00122feea
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75919173"
---
# <a name="ca1707-identifiers-should-not-contain-underscores"></a>CA1707: Tanımlayıcılar alt çizgi içermemelidir
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio ile ilgili en son belgeler için bkz. [CA1707: tanımlayıcılar alt çizgi içermemelidir](/visualstudio/code-quality/ca1707-identifiers-should-not-contain-underscores).

|||
|-|-|
|TypeName|IdentifiersShouldNotContainUnderscores|
|CheckId|CA1707|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Parçalara ayırma-derlemeler üzerinde ne zaman tetiklenir<br /><br /> Tür parametrelerine ne zaman kabarık olmayan|

## <a name="cause"></a>Sebep
 Bir tanımlayıcının adı, alt çizgi (_) karakterini içerir.

## <a name="rule-description"></a>Kural Tanımı
 Kural gereği, tanımlayıcı adlar alt çizgi (_) karakterini içermez. Kural ad alanlarını, türleri, üyeleri ve parametreleri denetler.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Adın tüm alt çizgi karakterlerini kaldırır.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

## <a name="related-rules"></a>İlgili kurallar
 [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar örnekten daha fazla farklı olmalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

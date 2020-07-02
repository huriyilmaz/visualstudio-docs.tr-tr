---
title: 'CA1713: olaylar ön eki veya sonraki öneki içermemelidir | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b05c39a9d8a4a004359baf63919eb427c25fa5d9
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85543968"
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Olaylar önce ya da sonra önekine sahip olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|
|CheckId|CA1713|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Bir olayın adı ' before ' veya ' After ' ile başlar.

## <a name="rule-description"></a>Kural Tanımı
 Olay adları, olayı oluşturan eylemi betimlemelidir. Belirli bir sırayla ilgili olayları adlandırmak için şimdiki veya geçmiş zamanı göreceli konumun sıralı eylemlerini belirtmek için kullanın. Örneğin, bir kaynağı kapatırken oluşan bir çift olayı adlandırırken, ' Beforeckaybetme ' ve ' AfterClose ' yerine ' Closing ' ve ' Closed ' adını yazabilirsiniz.

 Adlandırma kuralları, ortak dil çalışma zamanını hedefleyen kitaplıklar için ortak bir görünüm sağlar. Bu, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır ve müşterinin, kitaplığın yönetilen kod geliştirme konusunda uzmanlığa sahip olan birisi tarafından geliştirildiğini arttırır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Olay adından öneki kaldırın ve bir fiilin var olan veya geçmiş zaman hali kullanacak şekilde adı değiştirmeyi göz önünde bulundurun.

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın.

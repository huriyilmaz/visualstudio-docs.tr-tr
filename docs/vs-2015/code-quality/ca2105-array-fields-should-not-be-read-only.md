---
title: 'CA2105: dizi alanları salt okunmamalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA2105
- ArrayFieldsShouldNotBeReadOnly
helpviewer_keywords:
- ArrayFieldsShouldNotBeReadOnly
- CA2105
ms.assetid: 0bdc3421-3ceb-4182-b30c-a992fbfcc35d
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: 7599359899ca4860913b5bc0dd601fd06d9b8b54
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72666020"
---
# <a name="ca2105-array-fields-should-not-be-read-only"></a>CA2105: Dizi alanları salt okunur olmamalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|ArrayFieldsShouldNotBeReadOnly|
|CheckId|CA2105|
|Kategori|Microsoft.Security|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Sebep
 Bir diziyi tutan ortak veya korumalı bir alan salt okunurdur.

## <a name="rule-description"></a>Kural Tanımı
 Dizi içeren bir alana `readonly` ([!INCLUDE[vbprvb](../includes/vbprvb-md.md)]`ReadOnly`) değiştiricisini uyguladığınızda, alan farklı bir diziye başvuracak şekilde değiştirilemez. Bir dizinin öğeleri salt okunur bir alanda depolanmış olsa bile değiştirilebilir. Herkese açık bir şekilde erişilebilen salt yazılır bir dizinin öğelerine dayalı işlemler yapan veya kararları veren kod, açıktan yararlanılır bir güvenlik açığı içerebilir.

 Ortak bir alana sahip olmanın CA1051 tasarım kuralını da ihlal ettiğini unutmayın [: görünür örnek alanlarını bildirme](../code-quality/ca1051-do-not-declare-visible-instance-fields.md).

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural tarafından tanımlanan güvenlik açığını gidermek için, herkese açık bir şekilde erişilebilen salt okunurdur. Aşağıdaki yordamlardan birini kullanmanız önemle önerilir:

- Diziyi, değiştirilemeyen türü kesin belirlenmiş bir koleksiyonla değiştirin. Daha fazla bilgi için bkz. <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>.

- Ortak alanı, özel dizinin bir kopyasını döndüren bir yöntem ile değiştirin. Kodunuz kopyaya bağlı olmadığından, öğeler değiştirilirse bir tehlike yoktur.

  İkinci yaklaşımı seçerseniz, alanı bir özelliği ile değiştirmeyin; dizileri döndüren Özellikler performansı olumsuz etkiler. Daha fazla bilgi için bkz. [CA1819: Properties dizileri döndürmemelidir](../code-quality/ca1819-properties-should-not-return-arrays.md).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarının dışlanmasını kesinlikle önerilmez. Neredeyse bir salt okuma alanının içeriğinin önemli olmadığı neredeyse hiçbir senaryo meydana gelir. Bu durumda senaryonuz varsa iletiyi dışlamak yerine `readonly` değiştiricisini kaldırın.

## <a name="example"></a>Örnek
 Bu örnek, bu kuralı ihlal eden tehlikeleri gösterir. İlk bölüm, güvenli olmayan iki alan (`grades` ve `privateGrades`) içeren `MyClassWithReadOnlyArrayField`türü olan bir örnek kitaplık gösterir. Alan `grades` geneldir ve bu nedenle herhangi bir çağırana karşı savunmasız olur. `privateGrades` alan özeldir, ancak `GetPrivateGrades` yöntemi tarafından çağıranlara döndürüldüğünden güvenlik açığı devam etmektedir. `securePrivateGrades` alanı, `GetSecurePrivateGrades` yöntemi tarafından güvenli bir şekilde sunulur. İyi tasarım uygulamalarını izlemek için özel olarak bildirilmiştir. İkinci bölüm `grades` ve `privateGrades` üyelerinde depolanan değerleri değiştiren kodu gösterir.

 Örnek sınıf kitaplığı aşağıdaki örnekte görünür.

 [!code-csharp[FxCop.Security.ArrayFieldsNotReadOnly#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.ArrayFieldsNotReadOnly/cs/FxCop.Security.ArrayFieldsNotReadOnly.cs#1)]

## <a name="example"></a>Örnek
 Aşağıdaki kod, salt okuma dizisi güvenlik sorunlarını göstermek için örnek sınıf kitaplığını kullanır.

 [!code-csharp[FxCop.Security.TestArrayFieldsRead#1](../snippets/csharp/VS_Snippets_CodeAnalysis/FxCop.Security.TestArrayFieldsRead/cs/FxCop.Security.TestArrayFieldsRead.cs#1)]

 Bu örnekteki çıktı:

 **Değişiklik yapmadan önce: Notlar: 90, 90, 90 özel notlar: 90, 90, 90 Secure notlar, 90, 90, 90**
**değiştirildikten sonra: Notlar: 90, 555, 90 özel notlar: 90, 555, 90 güvenli notlar, 90, 90, 90**
## <a name="see-also"></a>Ayrıca Bkz.
 <xref:System.Array?displayProperty=fullName> <xref:System.Collections.ReadOnlyCollectionBase?displayProperty=fullName>

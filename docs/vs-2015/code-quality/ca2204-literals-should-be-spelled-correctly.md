---
title: 'CA2204: değişmez değerler doğru yazılmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- Literals should be spelled correctly
- CA2204
- LiteralsShouldBeSpelledCorrectly
helpviewer_keywords:
- CA2204
ms.assetid: b0bbcbb6-c92d-4c14-8ef7-9c8b38c791a6
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: d3e94f308936f898e555b1ad38e6a9d50051a276
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659547"
---
# <a name="ca2204-literals-should-be-spelled-correctly"></a>CA2204: Değişmez değerler doğru yazılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|||
|-|-|
|TypeName|LiteralsShouldBeSpelledCorrectly|
|CheckId|CA2204|
|Kategori|Microsoft. Usage|
|Yeni Değişiklik|Kırılmamış|

## <a name="cause"></a>Sebep
 Bir yöntem, yerelleştirilmiş bir dize gerektiren bir parametre veya özellikte kullanılan bir sabit dize geçirir ve sabit dize, Microsoft yazım denetleyicisi kitaplığı tarafından tanınmayan bir veya daha fazla sözcük içeriyor.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, aşağıdaki durumlardan biri veya daha fazlası doğru olduğunda bir parametreye veya özelliğe değer olarak geçirilen bir sabit dize denetler:

- Parametrenin veya özelliğin <xref:System.ComponentModel.LocalizableAttribute> özniteliği true olarak ayarlandı.

- Parametre veya özellik adı "metin", "Ileti" veya "başlık" içerir.

- Console. Write veya Console. WriteLine yöntemine geçirilen dize parametresinin adı "Value" ya da "Format" değeridir.

  Bu kural, değişmez dizeyi sözcük olarak ayrıştırır, bileşik sözcükleri simgeleştirerek her sözcüğün/belirtecin yazımını denetler. Ayrıştırma algoritması hakkında daha fazla bilgi için bkz. [CA1704: tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md).

  Varsayılan olarak, yazım denetleyicisinin Ingilizce (en) sürümü kullanılır.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için sözcüğün yazımını düzeltin veya sözcüğü özel bir sözlüğe ekleyin. Özel sözlüklerin nasıl kullanılacağı hakkında bilgi için bkz. [nasıl yapılır: kod analizi sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md).

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan uyarıyı bastırmayın. Doğru yazılmış sözcükler, yeni yazılım kitaplıkları için gereken öğrenme eğrisini azaltır.

## <a name="related-rules"></a>İlgili kurallar
 [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

 [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

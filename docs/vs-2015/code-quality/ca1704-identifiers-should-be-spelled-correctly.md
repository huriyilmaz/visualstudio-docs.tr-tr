---
title: 'CA1704: tanımlayıcılar doğru yazılmalıdır | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: reference
f1_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
helpviewer_keywords:
- CA1704
- IdentifiersShouldBeSpelledCorrectly
ms.assetid: f2c7a44d-1690-44ca-9cd0-681b04b12b2a
caps.latest.revision: 27
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: b5e078fc1bb7fe247d541e7695e98c2de76c2466
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85544072"
---
# <a name="ca1704-identifiers-should-be-spelled-correctly"></a>CA1704: Tanımlayıcılar doğru yazılmalıdır
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

|Öğe|Değer|
|-|-|
|TypeName|IdentifiersShouldBeSpelledCorrectly|
|CheckId|CA1704|
|Kategori|Microsoft. Naming|
|Yeni Değişiklik|Yeni|

## <a name="cause"></a>Nedeni
 Tanımlayıcının adı, Microsoft yazım denetleyicisi kitaplığı tarafından tanınmayan bir veya daha fazla sözcük içeriyor. Bu kural oluşturucuları veya Get ve set özellik erişimcileri gibi özel adlandırılmış üyeleri denetlemez.

## <a name="rule-description"></a>Kural Tanımı
 Bu kural, tanımlayıcıyı belirteçlere ayrıştırır ve her belirtecin yazımını denetler. Ayrıştırma algoritması aşağıdaki dönüşümleri gerçekleştirir:

- Büyük harfler yeni bir belirteç başlatır. Örneğin, Mynameisali, "My", "Name", "The", "ali" olarak simgeleştirir.

- Birden çok büyük harf için, son büyük harf yeni bir belirteç başlatır. Örneğin, Gudüzenleyici "GUI", "Düzenleyici" olarak simgeleştirir.

- Baştaki ve sondaki kesme işaretleri kaldırılır. Örneğin, ' sender ' simgeleştirir "sender".

- Alt çizgiler bir belirtecin sonunu işaret eder ve kaldırılır. Örneğin, "Hello", "World" olarak simgeleştirir Hello_world.

- Gömülü ve işaretleri kaldırılır. Örneğin,&"biçim" olarak simgeleştirir.

  Varsayılan olarak, yazım denetleyicisinin Ingilizce (en) sürümü kullanılır. Şu anda başka bir dil sözlüğü yok.

## <a name="how-to-fix-violations"></a>İhlaller Nasıl Düzeltilir?
 Bu kural ihlalini düzeltmek için sözcüğün yazımını düzeltin veya CustomDictionary.xml adlı özel bir sözlüğe sözcük ekleyin. Sözlüğü aracının yükleme dizinine, proje dizinine veya Kullanıcı profili altındaki araçla ilişkili dizine yerleştirin (%USERPROFILE%\Application Data \\ ...). İçindeki bir projeye özel sözlüğün nasıl ekleneceğini öğrenmek için [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] bkz. [nasıl yapılır: kod analizi sözlüğünü özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

- Sözlük/kelimeler/tanınan yol altında ihlale neden olmaması gereken sözcükler ekleyin.

- Sözlük/kelimeler/tanınmayan yol altında ihlalin neden olması gereken sözcükler ekleyin.

- Sözlük/kelimeler/kullanım dışı yol altında, eski olarak işaretlenmek zorunda olan sözcükler ekleyin. Bkz. ilgili kural konusu CA1726: daha fazla bilgi için [tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md).

- Sözlük/Kısaltmalar/CasingExceptions yoluna kısaltma büyük/küçük harf kuralları için özel durumlar ekleyin.

  Aşağıda, özel sözlük dosyası yapısına bir örnek verilmiştir.

```
<Dictionary>
   <Words>
      <Unrecognized>
         <Word>cb</Word>
      </Unrecognized>
      <Recognized>
         <Word>stylesheet</Word>
         <Word>GotDotNet</Word>
      </Recognized>
      <Deprecated>
         <Term PreferredAlternate="EnterpriseServices">ComPlus</Term>
      </Deprecated>
   </Words>
   <Acronyms>
      <CasingExceptions>
         <Acronym>CJK</Acronym>
         <Acronym>Pi</Acronym>
      </CasingExceptions>
   </Acronyms>
</Dictionary>
```

## <a name="when-to-suppress-warnings"></a>Uyarılar Bastırıldığında
 Bu kuraldan bir uyarıyı, yalnızca sözcüğün kasıtlı olarak yanlış yazıldığına ve sözcüğün sınırlı bir kitaplık kümesine uygulandığına karşı gizleyin. Doğru yazılmış sözcükler, yeni yazılım kitaplıkları için gerekli olan öğrenme eğrisini azaltır.

## <a name="related-rules"></a>İlgili kurallar
 [CA2204: Harfler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

 [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

 [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

 [CA1708: Tanımlayıcılar yalnızca büyük küçük harfle birbirinden farklı olmamalıdır](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)

 [CA1707: Tanımlayıcılar alt çizgi içermemelidir](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)

 [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)

## <a name="see-also"></a>Ayrıca Bkz.
 [Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme](../code-quality/how-to-customize-the-code-analysis-dictionary.md)

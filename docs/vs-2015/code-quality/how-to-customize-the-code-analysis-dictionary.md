---
title: 'Nasıl yapılır: kod analizi sözlüğünü özelleştirme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-code-analysis
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
caps.latest.revision: 23
author: jillre
ms.author: jillfra
manager: wpickett
ms.openlocfilehash: e3c8e8005a585e57f61ed873203305517d7b204a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72658628"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Kod Analizi, kodlardaki tanımlayıcıları yazım, dilbilgisi ve diğer adlandırma kurallarından hatalara karşı denetlemek için yerleşik bir sözlük kullanır [!INCLUDE[dnprdnshort](../includes/dnprdnshort-md.md)] . Yerleşik sözlüğe hüküm, kısaltmalar ve kısaltmalar eklemek, kaldırmak veya değiştirmek için özel bir sözlük XML dosyası oluşturabilirsiniz.

 Örneğin, kodunuzun **DoorKnokker**adlı bir sınıf içerdiğini varsayalım. Kod Analizi, adı iki sözcükten oluşan bir bileşim olarak belirler: **kapılı** ve **kker**. Daha sonra, **kker** 'ın doğru yazılmadığını belirten bir uyarı oluşturabilir. Kod analizini yazımı tanıyacak şekilde zorlamak için, özel sözlüğe **kker** terimini ekleyebilirsiniz.

## <a name="to-create-a-custom-dictionary"></a>Özel sözlük oluşturmak için
 **CustomDictionary.xml**adlı bir dosya oluşturun.

 Aşağıdaki XML yapısını kullanarak özel sözcüklerinizi tanımlayın:

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
         </Compound>
         <DiscreteExceptions>
            <Term></Term>
         </DiscreteExceptions>
      </Words>
      <Acronyms>
         <CasingExceptions>
            <Acronym></Acronym>
         </CasingExceptions>
      </Acronyms>
   </Dictionary>
```

## <a name="custom-dictionary-elements"></a>Özel sözlük öğeleri
 Özel sözlükte aşağıdaki öğelerin iç metni olarak terimler ekleyerek kod çözümleme sözlüğünün davranışını değiştirebilirsiniz:

- [Sözlük/sözcük/tanınan/Word](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Sözlük/sözcük/tanınmayan/sözcük](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Sözlük/sözcük/kullanım dışı/terim [ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Sözlük/sözcük/bileşik/terim [ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Sözlük/kelimeler/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Sözlük/Kısaltmalar/CasingExceptions/Kısaltma](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> Sözlük/sözcük/tanınan/Word
 Kod analizinin doğru yazılmış olarak tanımladığı koşullar listesine bir terim eklemek için, terimi bir sözlük/kelimeler/tanınan/Word öğesinin iç metni olarak ekleyin. Sözlük/sözcük/tanınan/Word öğelerinin terimleri büyük/küçük harfe duyarlı değildir.

 **Örnek**

```
<Dictionary>
      <Words>
         <Recognized>
            <Word>knokker</Word>
            ...
         </Recognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Sözlük/kelimeler/tanınan düğümlerdeki terimler aşağıdaki kod çözümleme kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204: Harfler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Sözlük/sözcük/tanınmayan/sözcük
 Kod analizinin doğru yazılmış olarak tanımladığı koşullar listesinden bir terimi dışlamak için, bir sözlük/sözcük/tanınmayan/Word öğesinin iç metni olarak hariç tutulacak terimi ekleyin. Sözlük/sözcük/tanınmayan/Word öğelerinin terimleri büyük/küçük harfe duyarlı değildir.

 **Örnek**

```
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>meth</Word>
            ...
         </Unrecognized>
         ...
      </Words>
      ...
</Dictionary>

```

 Sözlük/kelimeler/tanınmayan düğüm içindeki terimler aşağıdaki kod çözümleme kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)

- [CA2204: Harfler doğru yazılmalıdır](../code-quality/ca2204-literals-should-be-spelled-correctly.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Sözlük/sözcük/kullanım dışı/terim [ @PreferredAlternate ]
 Kod analizinin kullanım dışı olarak tanımladığı koşullar listesine bir terim eklemek için, terimi bir sözlük/kelimeler/kullanım dışı/terim öğesinin iç metni olarak ekleyin. Kullanım dışı bırakılan bir terim, doğru yazılmış ancak kullanılmamalıdır.

 Uyarı içinde önerilen bir alternatif terim eklemek için, term öğesinin Preferredalternatif özniteliğinde diğerini belirtin. Alternatif önermek istemiyorsanız öznitelik değerini boş bırakabilirsiniz.

- Sözlük/kelimeler/kullanım dışı/terim öğesindeki kullanım dışı olan dönem büyük/küçük harfe duyarlı değildir.

- Preferredalternatif öznitelik değeri büyük/küçük harfe duyarlıdır. Bileşik alternatifler için Pascal case kullanın.

  **Örnek**

```
<Dictionary>
      <Words>
         <Deprecated>
            <Term PreferredAlternate="LogOn">login</Term>
            ...
         </Deprecated>
         ...
      </Words>
      ...
</Dictionary>

```

 Sözlük/kelimeler/kullanım dışı düğüm içindeki terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726-use-preferred-terms.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Sözlük/sözcük/bileşik/terim [ @CompoundAlternate ]
 Yerleşik sözlük, bazı terimleri bileşik bir terim yerine tek ve ayrık terimler olarak tanımlar. Kod analizinin Birleşik bir sözcük olarak tanımladığı ve terimin doğru büyük küçük harflerini belirten terimler listesine bir terim eklemek için, terimi bir sözlük/sözcük/bileşik/terim öğesinin iç metni olarak ekleyin. Terim öğesinin Compoundalternatif özniteliğinde, tek tek sözcüklerin (Pascal Case) ilk harfini büyük harfe ayırarak bileşik terimi oluşturan tek kelimeleri belirtin. İç metinde belirtilen terimin otomatik olarak sözlüğe/sözcüklere/DiscreteExceptions listesine eklendiğini unutmayın.

- Sözlük/kelimeler/kullanım dışı/terim öğesindeki kullanım dışı olan dönem büyük/küçük harfe duyarlı değildir.

- Preferredalternatif öznitelik değeri büyük/küçük harfe duyarlıdır. Bileşik alternatifler için Pascal case kullanın.

  **Örnek**

```
<Dictionary>
      <Words>
         <Compound>
            <Term CompoundAlternate="CheckBox">checkbox</Term>
            ...
         </Compound>
         ...
      </Words>
      ...
</Dictionary>

```

 Sözlük/kelimeler/bileşik düğüm içindeki terimler aşağıdaki kod çözümleme kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Sözlük/kelimeler/DiscreteExceptions/Term
 Bir terimi, kod analizinin, Bileşik sözcüklerin büyük küçük harf kuralları tarafından denetlenme sırasında tek ve ayrı bir sözcük olarak tanımladığı bir terimi dışlamak için, terimi bir sözlük/kelimeler/DiscreteExceptions/Term öğesinin iç metni olarak ekleyin. Sözlük/kelimeler/DiscreteExceptions/Term öğesindeki terim büyük/küçük harfe duyarlı değildir.

 **Örnek**

```
<Dictionary>
      <Words>
         <DiscreteExceptions>
            <Term>checkbox</Term>
            ...
         </DiscreteExceptions>
         ...
      </Words>
      ...
</Dictionary>

```

 Sözlük/kelimeler/DiscreteExceptions düğümündeki terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Sözlük/Kısaltmalar/CasingExceptions/Kısaltma
 Kod analizinin doğru yazılmış olarak tanımladığı terimler listesine bir kısaltma eklemek ve terim Bileşik sözcüklerin büyük küçük harf kuralları tarafından denetlendiğinde kısaltmasının nasıl ekleneceğini belirtmek için, terimi bir Sözlük/Kısaltmalar/CasingExceptions/kısaltması öğesinin iç metni olarak ekleyin. Sözlük/Kısaltmalar/CasingExceptions/kısaltması öğesindeki kısaltma büyük/küçük harfe duyarlıdır.

 **Örnek**

```
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>

```

 Sözlük/Kısaltmalar/CasingExceptions düğümündeki terimler aşağıdaki kod çözümleme kurallarına uygulanır:

- [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Bir projeye özel bir sözlük uygulamak için

1. **Çözüm Gezgini**, aşağıdaki yordamlardan birini kullanın:

2. Tek bir projeye sözlük eklemek için, proje adına sağ tıklayın ve ardından **varolan öğeyi Ekle**' ye tıklayın. **Varolan öğe Ekle** iletişim kutusunda dosyayı belirtin.

3. İki veya daha fazla proje arasında paylaşılan bir sözlük eklemek için, **Varolan öğe Ekle** iletişim kutusunda paylaşılacak dosyayı bulun, **Ekle** düğmesinin üzerindeki aşağı oka tıklayın ve ardından **bağlantı olarak ekle**' ye tıklayın.

4. **Çözüm Gezgini**, **CustomDictionary.xml** dosya adına sağ tıklayın ve **Özellikler**' e tıklayın.

5. **Yapı eylemi** listesinden **codeanalysisdictionary**' yi seçin.

6. **Çıkış Dizinine Kopyala** listesinden **kopyalama**' yı seçin.

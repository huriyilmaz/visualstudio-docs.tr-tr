---
title: 'Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c3fbcbbfd52e4715dc6ee063ae0bae905eb3e65a
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75587530"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme

Kod Analizi, kodunuzun hatalarını yazım, dilbilgisi büyük/küçük harf ve diğer .NET Tasarım Yönergelerinin adlandırma kurallarına göre denetlemek için yerleşik bir sözlük kullanır. Yerleşik sözlüğe hüküm, kısaltmalar ve kısaltmalar eklemek, kaldırmak veya değiştirmek için özel bir sözlük XML dosyası oluşturabilirsiniz.

Örneğin, kodunuzun **DoorKnokker**adlı bir sınıf içerdiğini varsayalım. Kod Analizi, adı iki sözcükten oluşan bir bileşim olarak belirler: **kapılı** ve **kker**. Daha sonra, **kker** 'ın doğru yazılmadığını belirten bir uyarı oluşturabilir. Kod analizini yazımı tanıyacak şekilde zorlamak için, özel sözlüğe **kker** terimini ekleyebilirsiniz.

## <a name="to-create-a-custom-dictionary"></a>Özel sözlük oluşturmak için

**CustomDictionary. xml**adlı bir dosya oluşturun.

Aşağıdaki XML yapısını kullanarak özel sözcüklerinizi tanımlayın:

```xml
<Dictionary>
      <Words>
         <Unrecognized>
            <Word>knokker</Word>
         </Unrecognized>
         <Recognized>
            <Word></Word>
         </Recognized>
         <Deprecated>
            <Term PreferredAlternate=""></Term>
         </Deprecated>
         <Compound>
            <Term CompoundAlternate=""></Term>
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

- [Sözlük/sözcük/kullanım dışı/terim [@PreferredAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Sözlük/sözcük/bileşik/terim [@CompoundAlternate]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Sözlük/kelimeler/DiscreteExceptions/Term](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Sözlük/Kısaltmalar/CasingExceptions/Kısaltma](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="BKMK_DictionaryWordsRecognizedWord"></a>Sözlük/sözcük/tanınan/Word

Kod analizinin doğru yazılmış olarak tanımladığı koşullar listesine bir terim eklemek için, terimi bir sözlük/kelimeler/tanınan/Word öğesinin iç metni olarak ekleyin. Sözlük/sözcük/tanınan/Word öğelerinin terimleri büyük/küçük harfe duyarlı değildir.

**Örnek**

```xml
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

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)

- [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsUnrecognizedWord"></a>Sözlük/sözcük/tanınmayan/sözcük

Kod analizinin doğru yazılmış olarak tanımladığı koşullar listesinden bir terimi dışlamak için, bir sözlük/sözcük/tanınmayan/Word öğesinin iç metni olarak hariç tutulacak terimi ekleyin. Sözlük/sözcük/tanınmayan/Word öğelerinin terimleri büyük/küçük harfe duyarlı değildir.

**Örnek**

```xml
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

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)

- [CA2204: Değişmez değerler doğru yazılmalıdır](../code-quality/ca2204.md)

### <a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a>Sözlük/sözcük/kullanım dışı/terim [@PreferredAlternate]

Kod analizinin kullanım dışı olarak tanımladığı koşullar listesine bir terim eklemek için, terimi bir sözlük/kelimeler/kullanım dışı/terim öğesinin iç metni olarak ekleyin. Kullanım dışı bırakılan bir terim, doğru yazılmış ancak kullanılmamalıdır.

Uyarı içinde önerilen bir alternatif terim eklemek için, term öğesinin Preferredalternatif özniteliğinde diğerini belirtin. Alternatif önermek istemiyorsanız öznitelik değerini boş bırakabilirsiniz.

- Sözlük/kelimeler/kullanım dışı/terim öğesindeki kullanım dışı olan dönem büyük/küçük harfe duyarlı değildir.

- Preferredalternatif öznitelik değeri büyük/küçük harfe duyarlıdır. Bileşik alternatifler için Pascal case kullanın.

**Örnek**

```xml
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

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)

### <a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a>Sözlük/sözcük/bileşik/terim [@CompoundAlternate]

Yerleşik sözlük, bazı terimleri bileşik bir terim yerine tek ve ayrık terimler olarak tanımlar. Kod analizinin Birleşik bir sözcük olarak tanımladığı ve terimin doğru büyük küçük harflerini belirten terimler listesine bir terim eklemek için, terimi bir sözlük/sözcük/bileşik/terim öğesinin iç metni olarak ekleyin. Terim öğesinin Compoundalternatif özniteliğinde, tek tek sözcüklerin (Pascal Case) ilk harfini büyük harfe ayırarak bileşik terimi oluşturan tek kelimeleri belirtin. İç metinde belirtilen terimin otomatik olarak sözlüğe/sözcüklere/DiscreteExceptions listesine eklendiğini unutmayın.

- Sözlük/sözcük/bileşik/terim öğesindeki bileşik terim büyük/küçük harfe duyarlı değildir.

- Compoundalternatif öznitelik değeri büyük/küçük harfe duyarlıdır. Bileşik alternatifler için Pascal case kullanın.

**Örnek**

```xml
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

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeler doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

### <a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a>Sözlük/kelimeler/DiscreteExceptions/Term

Bir terimi, kod analizinin, Bileşik sözcüklerin büyük küçük harf kuralları tarafından denetlenme sırasında tek ve ayrı bir sözcük olarak tanımladığı bir terimi dışlamak için, terimi bir sözlük/kelimeler/DiscreteExceptions/Term öğesinin iç metni olarak ekleyin. Sözlük/kelimeler/DiscreteExceptions/Term öğesindeki terim büyük/küçük harfe duyarlı değildir.

**Örnek**

```xml
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

- [CA1701: Kaynak dize bileşik sözcüklerinin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin küçük/büyük harfleri doğru yazılmalıdır](../code-quality/ca1702.md)

### <a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a>Sözlük/Kısaltmalar/CasingExceptions/Kısaltma

Kod analizinin doğru yazılmış olarak tanımladığı terimler listesine bir kısaltma eklemek ve terim Bileşik sözcüklerin büyük küçük harf kuralları tarafından denetlendiğinde kısaltmasının nasıl ekleneceğini belirtmek için, terimi bir Sözlük/Kısaltmalar/CasingExceptions/kısaltması öğesinin iç metni olarak ekleyin. Sözlük/Kısaltmalar/CasingExceptions/kısaltması öğesindeki kısaltma büyük/küçük harfe duyarlıdır.

**Örnek**

```xml
<Dictionary>
      <Acronyms>
         <CasingExceptions>
            <Acronym>NESW</Acronym>   <!-- North East South West -->
            ...
         </CasingExceptions>
         ...
      </Acronyms>
      ...
</Dictionary>
```

Sözlük/Kısaltmalar/CasingExceptions düğümündeki terimler aşağıdaki kod çözümleme kurallarına uygulanır:

- [CA1709: Tanımlayıcıların büyük/küçük harfleri doğru yazılmalıdır](../code-quality/ca1709.md)

## <a name="BKMK_ToApplyACustomDictionaryToAProject"></a>Bir projeye özel bir sözlük uygulamak için

1. **Çözüm Gezgini**, aşağıdaki yordamlardan birini kullanın:

2. Tek bir projeye sözlük eklemek için, proje adına sağ tıklayın ve ardından **varolan öğeyi Ekle**' ye tıklayın. **Varolan öğe Ekle** iletişim kutusunda dosyayı belirtin.

3. İki veya daha fazla proje arasında paylaşılan bir sözlük eklemek için, **Varolan öğe Ekle** iletişim kutusunda paylaşılacak dosyayı bulun, **Ekle** düğmesinin üzerindeki aşağı oka tıklayın ve ardından **bağlantı olarak ekle**' ye tıklayın.

4. **Çözüm Gezgini**, **CustomDictionary. xml** dosya adına sağ tıklayın ve **Özellikler**' e tıklayın.

5. **Yapı eylemi** listesinden **codeanalysisdictionary**' yi seçin.

6. **Çıkış Dizinine Kopyala** listesinden **kopyalama**' yı seçin.

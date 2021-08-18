---
title: 'Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme'
ms.date: 11/04/2016
description: Yazım ve adlandırma kuralı hatalarını tanımlayan kod analizi sözlüğü hakkında bilgi edinebilirsiniz. Özel sözlük oluşturma ve bunu projeye uygulama hakkında bilgi.
ms.custom: SEO-VS-2020
ms.topic: how-to
helpviewer_keywords:
- code analysis dictionary
- custom dictionary, code analysis
- dictionary, code analysis
ms.assetid: 667e3b4e-beff-48be-b3d1-376e1716a895
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.technology: vs-ide-code-analysis
ms.workload:
- multiple
ms.openlocfilehash: f22d14e5cfeff8bc79327d62a10abd9a54c8bf2b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147420"
---
# <a name="how-to-customize-the-code-analysis-dictionary"></a>Nasıl yapılır: Kod Çözümleme Dizinini Özelleştirme

Code Analysis yazım hataları, dilbilgisi büyük/küçük harf ve .NET tasarım yönergelerinin diğer adlandırma kuralları için kodundaki tanımlayıcıları kontrol etmek için yerleşik bir sözlük kullanır. Yerleşik sözlüğe terim, kısaltma ve kısaltma eklemek, kaldırmak veya değiştirmek için özel bir sözlük Xml dosyası oluşturabilirsiniz.

Örneğin, kodunuzun **DoorKnokker adlı bir sınıf içerdiğini varsayalım.** Code Analysis iki sözcüklü bileşik olarak tanımlayabilirsiniz: **door** ve **knokker**. Daha sonra **knokker'ın doğru yazılmış** olmadığının bir uyarıya neden olur. Kod analizini yazım tanımaya zorlamak için özel sözlüğe **knokker** terimini ekleyebilirsiniz.

## <a name="to-create-a-custom-dictionary"></a>Özel sözlük oluşturmak için

CustomDictionary.xmladlı bir **dosya oluşturun.**

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

## <a name="custom-dictionary-elements"></a>Özel Sözlük Öğeleri

Özel sözlükte aşağıdaki öğelerin Code Analysis olarak terimler ekleyerek sözlüğünün davranışını değiştirebilirsiniz:

- [Sözlük/Sözcükler/Tanınan/Sözcük](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsRecognizedWord)

- [Sözlük/Sözcükler/Tanınmayan/Sözcük](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsUnrecognizedWord)

- [Sözlük/Sözcükler/Kullanım Dışı/Terim[ @PreferredAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDeprecatedTermPreferredAlternate)

- [Sözlük/Sözcükler/Bileşik/Terim[ @CompoundAlternate ]](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsCompoundTermCompoundAlternate)

- [Sözlük/Sözcükler/DiscreteExceptions/Terim](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryWordsDiscreteExceptionsTerm)

- [Sözlük/Kısaltmalar/CasingExceptions/Kısaltma](../code-quality/how-to-customize-the-code-analysis-dictionary.md#BKMK_DictionaryAcronymsCasingExceptionsAcronym)

### <a name="dictionarywordsrecognizedword"></a><a name="BKMK_DictionaryWordsRecognizedWord"></a> Sözlük/Sözcükler/Tanınan/Sözcük

Kod analizinin doğru yazım olarak tanımlıyor olduğu terimler listesine bir terim eklemek için terimi bir Sözlük/Sözcükler/Tanınan/Word öğesinin iç metni olarak ekleyin. Sözlük/Sözcükler/Tanınan/Word öğelerinde terimler büyük/büyük/büyük harfe duyarlı değildir.

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

Sözlük/Sözcükler/Tanınan düğümler'de terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

- [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)

- [CA2204: Harfler doğru yazılmalıdır](../code-quality/ca2204.md)

### <a name="dictionarywordsunrecognizedword"></a><a name="BKMK_DictionaryWordsUnrecognizedWord"></a> Sözlük/Sözcükler/Tanınmayan/Sözcük

Bir terimi kod analizinin doğru yazım olarak tanımlayan terimler listesinden dışlamak için, dışlanan terimi bir Sözlük/Sözcükler/Tanınmayan/Word öğesinin iç metni olarak ekleyin. Sözlük/Sözcükler/Tanınmayan/Word öğelerinde terimler büyük/büyük/büyük harfe duyarlı değildir.

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

Sözlük/Sözcükler/Tanınmayan düğümdeki terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

- [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)

- [CA2204: Harfler doğru yazılmalıdır](../code-quality/ca2204.md)

### <a name="dictionarywordsdeprecatedtermpreferredalternate"></a><a name="BKMK_DictionaryWordsDeprecatedTermPreferredAlternate"></a> Sözlük/Sözcükler/Kullanım Dışı/Terim[ @PreferredAlternate ]

Kod analizinin kullanım dışı olarak tanımeceği terimler listesine bir terim eklemek için terimi bir Sözlük/Sözcükler/Kullanım Dışı/Terim öğesinin iç metni olarak ekleyin. Kullanım dışı bir terim, doğru yazılmış ancak kullanılmamış bir sözcüktir.

Uyarıya önerilen alternatif bir terim eklemek için Term öğesinin PreferredAlternate özniteliğinde alternatifini belirtin. Alternatif önermek istemiyorsanız öznitelik değerini boş bırakın.

- Dictionary/Words/Deprecated/Term öğesinde kullanım dışı terimi büyük/büyük/büyük harfe duyarlı değildir.

- PreferredAlternate öznitelik değeri büyük/büyük/büyük harfe duyarlıdır. Bileşik alternatifler için Pascal case kullanın.

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

Sözlük/Sözcükler/Kullanım Dışı düğümünde yer alan terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

- [CA1726: Tercih edilen terimleri kullanın](../code-quality/ca1726.md)

### <a name="dictionarywordscompoundtermcompoundalternate"></a><a name="BKMK_DictionaryWordsCompoundTermCompoundAlternate"></a> Sözlük/Sözcükler/Bileşik/Terim[ @CompoundAlternate ]

Yerleşik sözlük, bazı terimleri bileşik terim yerine tek, ayrık terimler olarak tanımlar. Kod analizinin bileşik sözcük olarak tanımlayan terimler listesine bir terim eklemek ve terimin doğru büyük/küçük/küçüklüğünü belirtmek için terimi Sözlük/Sözcükler/Bileşik/Terim öğesinin iç metni olarak ekleyin. Term öğesinin CompoundAlternate özniteliğinde, tek tek sözcüklerin (Pascal büyük/sn) ilk harfini büyük harfle yazarak bileşik terimin tek tek sözcüklerini belirtin. İç metinde belirtilen terimin Sözlük/Sözcükler/DiscreteExceptions listesine otomatik olarak eklenmiştir.

- Sözlük/Sözcükler/Bileşik/Terim öğesinde bileşik terim büyük/büyük/büyük harfe duyarlı değildir.

- CompoundAlternate öznitelik değeri büyük/büyük/büyük harfe duyarlıdır. Bileşik alternatifler için Pascal case kullanın.

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

Sözlük/Sözcükler/Bileşik düğümdeki terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702.md)

- [CA1703: Kaynak dizeleri doğru yazılmalıdır](../code-quality/ca1703.md)

- [CA1704: Tanımlayıcılar doğru yazılmalıdır](../code-quality/ca1704.md)

### <a name="dictionarywordsdiscreteexceptionsterm"></a><a name="BKMK_DictionaryWordsDiscreteExceptionsTerm"></a> Sözlük/Sözcükler/DiscreteExceptions/Terim

Terim bileşik sözcükler için büyük/küçük resim kuralları tarafından denetlenirken, kod analizinin tek, ayrık sözcük olarak tanımlayan terimler listesinde bir terimi dışlamak için terimi Bir Sözlük/Sözcükler/DiscreteExceptions/Term öğesinin iç metni olarak ekleyin. Dictionary/Words/DiscreteExceptions/Term öğesinde terimi büyük/büyük/büyük harfe duyarlı değildir.

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

Sözlük/Sözcükler/DiscreteExceptions düğümünde yer alan terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1701: Kaynak dizesi bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1701.md)

- [CA1702: Bileşik sözcüklerin büyük küçük harfleri doğru olmalıdır](../code-quality/ca1702.md)

### <a name="dictionaryacronymscasingexceptionsacronym"></a><a name="BKMK_DictionaryAcronymsCasingExceptionsAcronym"></a> Sözlük/Kısaltmalar/CasingExceptions/Kısaltma

Kod analizinin doğru yazım olarak tanımlayan terimler listesine bir kısaltma eklemek ve terimin bileşik sözcükler için büyük/küçük harf kuralları tarafından denetlenen kısaltmayı belirtmek için terimi bir Dictionary/Acronyms/CasingExceptions/Acronym öğesinin iç metni olarak ekleyin. Dictionary/Acronyms/CasingExceptions/Acronym öğesinde yer alan kısaltma büyük/büyük/büyük harfe duyarlıdır.

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

Sözlük/Kısaltmalar/CasingExceptions düğümünde yer alan terimler aşağıdaki kod analizi kurallarına uygulanır:

- [CA1709: Tanımlayıcılar doğru büyük küçük harfe sahip olmalıdır](../code-quality/ca1709.md)

## <a name="to-apply-a-custom-dictionary-to-a-project"></a><a name="BKMK_ToApplyACustomDictionaryToAProject"></a> Projeye özel sözlük uygulamak için

1. Bu **Çözüm Gezgini,** aşağıdaki yordamlardan birini kullanın:

    - Tek bir projeye sözlük eklemek için proje adına sağ tıklayın ve ardından Var Olan Öğeyi **Ekle'ye tıklayın.** Dosyayı Var Olan Öğe **Ekle iletişim kutusunda** belirtin.
  
    - İki veya daha fazla proje arasında paylaşılan bir sözlük eklemek için  Var Olan Öğe Ekle iletişim kutusunda  paylaşılacak dosyayı bulun, Ekle düğmesinde aşağı oka tıklayın ve Ardından Bağlantı **Ekle'ye tıklayın.**

2. Bu **Çözüm Gezgini,** dosya adına sağ **CustomDictionary.xml** ve Özellikler'e **tıklayın.**

3. Derleme Eylemi listesinde **CodeAnalysisDictionary öğesini seçin.** 

4. Çıkış **Dizinine Kopyala listesinde** **Kopyalama'ya tıklayın.**

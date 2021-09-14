---
title: 'Nasıl Yapılır: XML Kod Parçacıkları Oluşturma'
description: XML dosyalarını daha hızlı oluşturmanıza olanak Visual Studio XML kod parçacıkları oluşturmak için xml düzenleyicisini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: ee6dfe8990cf5e85a35a0d538c2bfbd50c3462e4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126633625"
---
# <a name="how-to-create-xml-snippets"></a>Nasıl yapılır: XML kod parçacıkları oluşturma

XML düzenleyicisi, yeni XML kod parçacıkları oluşturmak için kullanılabilir. Düzenleyici, yeni XML kod parçacıkları oluşturmak için ortak kod parçacığı olan "Kod Parçacığı" adlı bir XML kod parçacığı içerir.

## <a name="to-create-a-new-xml-snippet"></a>Yeni bir XML kod parçacığı oluşturmak için

Yeni bir XML kod parçacığı oluşturmak için yeni bir XML dosyası oluşturun ve Kod Parçacığı **Ekle özelliğini** kullanın.

1. Dosya menüsünde **Yeni'ye** ve **ardından** Dosya'ya **tıklayın.**

2. **XML Dosyası'nın ardından** Aç'a **tıklayın.**

3. Düzenleyici bölmesine sağ tıklayın ve Kod Parçacığı **Ekle'yi seçin.**

4. Listeden **Kod Parçacığı'ı** seçin ve Enter tuşuna **basın.**

5. Yeni kod parçacığında herhangi bir değişiklik yapın.

6. Dosya **menüsünden Kaydet'i** **XMLFile.xml.**

     Dosyayı **Farklı Kaydet** iletişim kutusu görüntülenir.

7. Yeni kod parçacığının adını girin ve Tür **olarak kaydet açılan** **penceresinden Kod Parçacığı** Dosyaları'ı seçin.

8. Dosya **konumunu** *Belgelerim\Visual Studio 2005\Code Snippets\XML\Xml Kod* Parçacıklarım klasörü olarak değiştirmek için Save in açılan listesini kullanın ve ardından **Kaydet'e basın.**

## <a name="snippet-description"></a>Kod parçacığı açıklaması

Bu bölümde, ortak kod parçacığında bazı önemli öğeler açık almaktadır. XML kod parçacıkları tarafından kullanılan şema öğeleri hakkında daha fazla bilgi için [bkz. Kod parçacıkları şema başvurusu.](../ide/code-snippets-schema-reference.md)

### <a name="snippettype-element"></a>SnippetType öğesi

Düzenleyici iki kod parçacığı türü destekler:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

Tür, `Expansion` Kod Parçacığı Ekle komutunu çağırarak kod parçacığının **görüntülendiğinde görünür olup olmadığını** belirler. türü, `SurroundsWith` Surrounds With komutunu çağırarak kod parçacığının **görüntülendiğinde görüntü olup olmadığını** belirler.

### <a name="code-element"></a>Kod öğesi

`Code`öğesi, kod parçacığı çağrıldığında eklenecek XML metnini tanımlar.

> [!NOTE]
> XML kod parçacığı metninin bir bölüm içine alınmış olması `<![CDATA[...]]>` gerekir.

Aşağıdaki, ortak `Code` kod parçacığı tarafından oluşturulan öğesidir.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

öğesi `Code` üç değişken içerir.

- $name$ kullanıcı tanımlı değişkendir. Varsayılan olarak `name` "name" olan düzenlenebilir bir değere sahip olan bir öğesi oluşturur. Kullanıcı tanımlı değişkenler öğesi kullanılarak `Literal` tanımlanır.

- $selected$ önceden tanımlanmış bir değişkendir. Kod parçacığını faturalamadan önce XML düzenleyicisinde seçilen metni temsil eder. Bu değişkenin yerleşimi, seçilen metnin bu seçimi çevreleyen kod parçacığında nerede görüntülendiğinden emin olur.

- $end$ önceden tanımlanmış bir değişkendir. Kullanıcı kod parçacığı alanlarını düzenlemeyi tamamlamak için **Enter** tuşuna bassa, bu değişken giriş(^) değerinin nereye taşındığını belirler.

  Yukarıdaki `Code` öğe aşağıdaki XML metnini ekler:

```xml
<test>
  <name>name</name>
</test>
```

Name öğesinin değeri düzenlenebilir bir bölge olarak işaretlenir.

### <a name="literal-element"></a>Değişmez öğe

`Literal`öğesi, dosyaya eklendikten sonra özelleştirebileceğiniz değiştirme metnini tanımlamak için kullanılır. Örneğin, değişmez değer dizeleri, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilebilirsiniz. XML kod parçacığında herhangi bir sayıda değişmez öğe tanımlayabilir ve kod parçacığının içinde birden çok kez başvurarak bunları tanımlayabilirsiniz. Aşağıda, varsayılan değeri `Literal` "name" olan bir $name$ değişkeni tanımlayan bir öğe örneği ve bir örnektir.

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Değişmez değişmezler işlevlere de başvurabilirsiniz. XML düzenleyicisi **LookupPrefix** adlı bir işlev içerir. **LookupPrefix** işlevi, verilen ad alanı URI'sini xml belgesinde bu kod parçacığının çağrıldığında bulunduğu konumdan aratır ve varsa bu ad alanı için tanımlanan ad alanı ön ekini döndürür ve iki nokta üst üste :) bu adla. Aşağıda `Literal` LookupPrefix işlevini kullanan bir öğe örneği ve ardından ve ardından ve ve ardından bir öğe ve daha fazla bilgi ve saat **20:00'de 100'e** kadar 100.000 abd

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

$prefix$ değişkeni daha sonra XML kod parçacığının başka bir yerinde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML kod parçacıkları](../xml-tools/xml-snippets.md)
- [Nasıl yapılır: XML kod parçacıklarını kullanma](../xml-tools/how-to-use-xml-snippets.md)
- [Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)

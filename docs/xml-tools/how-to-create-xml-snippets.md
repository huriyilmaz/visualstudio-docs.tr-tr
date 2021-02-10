---
title: 'Nasıl Yapılır: XML Kod Parçacıkları Oluşturma'
description: XML dosyalarını daha hızlı bir şekilde oluşturmanızı sağlayan XML kod parçacıkları oluşturmak için Visual Studio 'da XML düzenleyicisini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: d8556dd7-1382-4af7-ba80-3e873c9416be
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ad907175f0826a5dd040f77c03517e00d4e1391c
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99959785"
---
# <a name="how-to-create-xml-snippets"></a>Nasıl yapılır: XML parçacıkları oluşturma

XML Düzenleyicisi, yeni XML parçacıkları oluşturmak için kullanılabilir. Düzenleyici, yeni XML parçacıkları oluşturmak için ortak bir kod parçacığı olan "kod parçacığı" adlı bir XML kod parçacığı içerir.

## <a name="to-create-a-new-xml-snippet"></a>Yeni bir XML kod parçacığı oluşturmak için

Yeni bir XML kod parçacığı oluşturmak için yeni bir XML dosyası oluşturun ve **kod parçacığı Ekle** özelliğini kullanın.

1. **Dosya** menüsünde **Yeni** ' ye ve ardından **Dosya**' ya tıklayın.

2. **XML dosyası** ' na ve sonra **Aç**' a tıklayın.

3. Düzenleyici bölmesine sağ tıklayın ve **kod parçacığı Ekle**' yi seçin.

4. Listeden **kod parçacığı** öğesini seçin ve **ENTER** tuşuna basın.

5. Yeni kod parçacığında herhangi bir değişiklik yapın.

6. **Dosya** menüsünden **Kaydet XMLFile.xml**' yi seçin.

     **Dosyayı farklı kaydet** iletişim kutusu görüntülenir.

7. Yeni kod parçacığının adını girin ve **farklı kaydet türü** açılan penceresinden **kod parçacığı dosyalarını** seçin.

8. Dosya konumunu, *My Studio 2005 \ Code SNIPPETS\XML\MY XML parçacıkları* klasörü olarak değiştirmek için Kaydet açılan listesini kullanın ve ardından **Kaydet** **'** e basın.

## <a name="snippet-description"></a>Kod parçacığı açıklaması

Bu bölümde ortak kod parçacığında bazı önemli öğeler açıklanmaktadır. XML parçacıkları tarafından kullanılan şema öğeleri hakkında daha fazla bilgi için bkz. [kod parçacıkları şema başvurusu](../ide/code-snippets-schema-reference.md).

### <a name="snippettype-element"></a>SnippetType Öğesi

Düzenleyici iki kod parçacığı türünü destekler:

```xml
<SnippetTypes>
  <SnippetType>SurroundsWith</SnippetType>
  <SnippetType>Expansion</SnippetType>
</SnippetTypes>
```

`Expansion`Tür **parçacığı Ekle** komutunu çağırdığınızda kod parçacığının görünüp görünmeyeceğini belirler. `SurroundsWith`Türü, komut **Ile çevrelerle** çağırdığınızda parçacığın görünüp görünmeyeceğini belirler.

### <a name="code-element"></a>Kod öğesi

`Code`Öğesi, kod parçacığı çağrıldığında eklenecek XML metnini tanımlar.

> [!NOTE]
> XML kod parçacığı metni bir bölümü içine alınmalıdır `<![CDATA[...]]>` .

`Code`Ortak parçacığı tarafından oluşturulan öğe aşağıda verilmiştir.

```xml
<Code Language="XML">
  <![CDATA[<test>
  <name>$name$</name>
  $selected$ $end$</test>]]>
</Code>
```

`Code`Öğesi üç değişken içerir.

- $name $ Kullanıcı tanımlı değişkendir. `name`Varsayılan olarak "Name" olan düzenlenebilir bir değere sahip bir öğesi oluşturur. Kullanıcı tanımlı değişkenler öğesi kullanılarak tanımlanır `Literal` .

- $selected $ önceden tanımlanmış bir değişkendir. Kod parçacığını çağırmadan önce XML düzenleyicisinde seçilen metni temsil eder. Bu değişkenin yerleştirilmesi, seçilen metnin, bu seçimi çevreleyen kod parçacığında nerede göründüğünü belirler.

- $end $ önceden tanımlanmış bir değişkendir. Kod parçacığı alanlarını Düzenlemeden sonra Kullanıcı ENTER tuşuna bastığında bu değişken, **giriş** işaretinin (^) nereye taşındığını belirler.

  Yukarıdaki `Code` öğe AŞAĞıDAKI XML metnini ekler:

```xml
<test>
  <name>name</name>
</test>
```

Name öğesinin değeri düzenlenebilir bir bölge olarak işaretlenir.

### <a name="literal-element"></a>Literal öğesi

`Literal`Öğesi, dosyaya eklendikten sonra özelleştirilebilecek değiştirme metnini belirlemek için kullanılır. Örneğin, değişmez dizeler, sayısal değerler ve bazı değişken adları değişmez değer olarak bildirilemez. XML kod parçacığınızdan herhangi bir sayıda sabit değer tanımlayabilir ve kod parçacığının içinden birden çok kez başvurabilirsiniz. Aşağıda, `Literal` varsayılan değeri "Name" olan $Name $ değişkenini tanımlayan bir öğe örneği verilmiştir.

```xml
<Literal>
  <ID>name</ID>
  <Default>name</Default>
</Literal
```

Değişmez değerler, işlevlere da başvurabilir. XML Düzenleyicisi **LookupPrefix** adlı bir işlev içerir. **LookupPrefix** işlevi, bu kod PARÇACıĞıNıN çağrıldığı XML belgesindeki konumdan verilen ad alanı URI 'sini arar ve bu ad alanı için tanımlanan ad alanı önekini (varsa) döndürür ve iki nokta üst üste ekler (:) Bu adda. Aşağıda `Literal` **LookupPrefix** işlevini kullanan bir öğe örneği verilmiştir.

```xml
<Literal Editable="false">
   <ID>prefix</ID>
   <Function>LookupPrefix("namespaceURI")</Function>
</Literal>
```

$Prefix $ değişkeni daha sonra XML kod parçacığındaki başka bir yerde kullanılabilir.

## <a name="see-also"></a>Ayrıca bkz.

- [XML kod parçacıkları](../xml-tools/xml-snippets.md)
- [Nasıl yapılır: XML kod parçacıklarını kullanma](../xml-tools/how-to-use-xml-snippets.md)
- [Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma](../xml-tools/how-to-generate-an-xml-snippet-from-an-xml-schema.md)

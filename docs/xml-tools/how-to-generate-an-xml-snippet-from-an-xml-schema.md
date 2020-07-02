---
title: 'Nasıl Yapılır: XML Şemasından XML Kod Parçacığı Oluşturma'
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: 2c128d2a-aaa6-4814-aa95-e07056afe338
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3c7dff8e1bb211343ccc44e0d1fd33d96c102283
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85817183"
---
# <a name="how-to-generate-an-xml-snippet-from-an-xml-schema"></a>Nasıl yapılır: XML şemasından XML kod parçacığı oluşturma

XML Düzenleyicisi bir XML şeması tanım dili (XSD) şemasından XML parçacıkları oluşturma özelliğine sahiptir. Örneğin, bir XML dosyası yazarken, öğe adının yanına konumlarken, öğeyi ilgili öğenin şema bilgilerinde oluşturulan XML verileriyle doldurmak için **Tab** tuşuna basabilirsiniz.

Bu özellik yalnızca öğelerde kullanılabilir. Aşağıdaki kurallar da geçerlidir:

- Öğesi ilişkili bir şema türüne sahip olmalıdır; diğer bir deyişle, öğe ilişkili şemaya göre geçerli olmalıdır. Şema türü soyut olamaz ve tür gereken öznitelikleri ve/veya gerekli alt öğeleri içermelidir.

- Düzenleyicideki geçerli öğe, hiçbir öznitelik olmadan boş olmalıdır. Örneğin, aşağıdakiler geçerlidir

  - `<Account`

  - `<Account>`

  - `<Account></Account>`

- İmleç, öğe adının hemen sağına yerleştirilmelidir.

Oluşturulan kod parçacığı tüm gerekli öznitelikleri ve öğeleri içerir. Birden `minOccurs` büyükse, en fazla 100 örneğe kadar, o öğenin gereken minimum örnek sayısı kod parçacığına dahil edilir. Şemada bulunan sabit değerler, kod parçacığında sabit değerlerle sonuçlanır. `xsd:any`ve `xsd:anyAttribute` öğeleri yok sayılır ve ek kod parçacığı yapıları gerektirmez.

Varsayılan değerler oluşturulur ve düzenlenebilir değerler olarak belirtilmiştir. Şema varsayılan bir değer belirtiyorsa, bu varsayılan değer kullanılır. Ancak, şema varsayılan değeri boş bir dize ise, düzenleyici varsayılan değerleri aşağıdaki şekilde oluşturur:

- Şema türü herhangi bir numaralandırma modeli içeriyorsa, doğrudan veya dolaylı olarak bir birleşim türü üye aracılığıyla, şema nesne modelinde bulunan ilk Numaralandırılmış değer varsayılan olarak kullanılır.

- Şema türü Atomik bir tür ise, düzenleyici Atomik türü alır ve atomik tür adını ekler. Türetilmiş basit bir tür için temel basit türü kullanır. Bir liste türü için atomik tür ' dir `itemType` . Bir birleşim için atomik tür, birinconun atomik türüdür `memberType` .

## <a name="example"></a>Örnek

Bu bölümdeki adımlarda, XML düzenleyicisinin şema tarafından oluşturulan XML kod parçacığı özelliğinin nasıl kullanılacağı gösterilmektedir.

> [!NOTE]
> Bu yordamları başlatmadan önce, şema dosyasını yerel bilgisayarınıza kaydedin.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Yeni bir XML dosyası oluşturmak ve bir XML şeması ile ilişkilendirmek için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Dosya**' ya tıklayın.

2. **Şablonlar** bölmesinde **XML dosyası** ' nı seçin ve **Aç**' a tıklayın.

     Düzenleyicide yeni bir dosya açılır. Dosya varsayılan bir XML bildirimi içerir `<?xml version="1.0" encoding="utf-8">` .

3. Belge Özellikleri penceresinde, **şemalar** alanındaki (**...**) düğmesine tıklayın.

     **Xsd şemaları** iletişim kutusu görüntülenir.

4. **Ekle**'ye tıklayın.

     **XSD şeması aç** iletişim kutusu görüntülenir.

5. Şema dosyasını seçin ve **Aç**' a tıklayın.

6. **Tamam**'a tıklayın.

     XML şeması artık XML belgesiyle ilişkili.

### <a name="to-generate-an-xml-snippet"></a>XML parçacığı oluşturmak için

1. `<`Düzenleyici bölmesine yazın.

2. Üyeler listesi olası öğeleri görüntüler:

     yorum eklemek için **!--** .

     **! **Belge türü eklemek IÇIN DOCTYPE.

     **?** bir işleme yönergesi eklemek için.

     Kök öğeyi eklemek için **Iletişim kurun** .

3. Üye listesinden **kişi** ' yi seçin ve **ENTER**tuşuna basın.

     Düzenleyici başlangıç etiketini ekler `<Contact` ve imleci öğe adından sonra konumlandırır.

4. Şema bilgilerine göre öğesi için XML verisi oluşturmak için **Tab** tuşuna basın `Contact` .

## <a name="input"></a>Girdi

Aşağıdaki şema dosyası, izlenecek yol tarafından kullanılır.

```xml
<?xml version="1.0" encoding="utf-8" ?>
<xs:schema elementFormDefault="qualified"
           xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:simpleType name="phoneType">
    <xs:restriction base="xs:string">
      <xs:enumeration value="Voice"/>
      <xs:enumeration value="Fax"/>
      <xs:enumeration value="Pager"/>
    </xs:restriction>
  </xs:simpleType>
  <xs:element name="Contact">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="Name">
          <xs:simpleType>
            <xs:restriction base="xs:string"></xs:restriction>
          </xs:simpleType>
        </xs:element>
        <xs:element name="Title"
                    type="xs:string" />
        <xs:element name="Phone"
                    minOccurs="1"
                    maxOccurs="unbounded">
          <xs:complexType>
            <xs:sequence>
              <xs:element name="Number"
                          minOccurs="1">
                <xs:simpleType>
                  <xs:restriction base="xs:string"></xs:restriction>
                </xs:simpleType>
              </xs:element>
              <xs:element name="Type"
                          default="Voice"
                          minOccurs="1"
                          type="phoneType"/>
            </xs:sequence>
          </xs:complexType>
        </xs:element>
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

### <a name="output"></a>Çıktı

Aşağıda öğesiyle ilişkili şema bilgilerine göre oluşturulan XML verileri verilmiştir `Contact` . `bold`XML kod parçacığında düzenlenebilir alanları belirleyin olarak işaretlenen öğeler.

```xml
<Contact>
  <Name>name</Name>
  <Title>title</Title>
  <Phone>
    <Number>number</Number>
    <Type>Voice</Type>
  </Phone>
</Contact>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML kod parçacıkları](../xml-tools/xml-snippets.md)
- [Nasıl yapılır: XML kod parçacıklarını kullanma](../xml-tools/how-to-use-xml-snippets.md)

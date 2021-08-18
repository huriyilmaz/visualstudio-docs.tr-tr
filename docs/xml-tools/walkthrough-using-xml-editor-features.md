---
title: 'İzlenecek yol: XML Düzenleyicisi özelliklerini kullanma'
description: Bu izlenecek yolda XML düzenleyicisinin özelliklerini gösteren adımları izleyerek yeni bir XML belgesi oluşturmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xml-tools
ms.workload:
- multiple
ms.openlocfilehash: 563f629ed21d524eb302d55af2550c86a89922e5
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045508"
---
# <a name="walkthrough-use-xml-editor-features"></a>İzlenecek yol: XML düzenleyicisi özelliklerini kullanma

Bu izlenecek yolda, yeni bir XML belgesi oluşturma adımları gösterilmektedir. İzlenecek yol, XML Düzenleyicisi 'nin XML yazma için değerli hale getirme özelliklerini de kullanır.

> [!NOTE]
> İzlenecek yolu başlatmadan önce, *HireDate. xsd* dosyasını (Bu konuya aşağıda verilmiştir) yerel bilgisayarınıza kaydedin.

## <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Yeni bir XML dosyası oluşturmak ve bir XML şeması ile ilişkilendirmek için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Dosya**' ya tıklayın.

2. **Şablonlar** bölmesinde **XML dosyası** ' nı seçin ve **Aç**' a tıklayın.

     Düzenleyicide yeni bir dosya açılır. Dosya varsayılan bir XML bildirimi içerir `<?xml version="1.0" encoding="utf-8">` .

3. Belge Özellikleri penceresinde, **şemalar** alanındaki (**...**) düğmesine tıklayın.

     **Xsd şemaları** iletişim kutusu görüntülenir.

4. **Ekle**'ye tıklayın.

     **XSD şeması aç** iletişim kutusu görüntülenir.

5. *HireDate. xsd* dosyasını seçin ve **Aç**' a tıklayın.

6. **Tamam**'a tıklayın.

     XML şeması artık XML belgesiyle ilişkili. XML şeması belgeyi doğrulamak için kullanılır. IntelliSense tarafından geçerli öğelerin üye listesini doldurmak için de kullanılır.

## <a name="to-add-data"></a>Veri eklemek için

1. `<`Düzenleyici bölmesine yazın.

     Üyeler listesi olası öğeleri görüntüler:

    - yorum eklemek için **!--** .

    - **!** Belge türü eklemek IÇIN DOCTYPE.

    - **?** bir işleme yönergesi eklemek için.

    - kök öğeyi eklemek için **çalışan** .

2. Açıklama düğümü eklemek için **&lt; !--** seçin ve **ENTER** tuşuna basın.

     Düzenleyici bir açıklama sonu etiketi ekler ve imleci başlangıç ve bitiş açıklaması etiketleri arasına yerleştirir.

3. **Test XML dosyasına** yazın.

4. Yeni bir satıra yazın `<` ve üye listesinden **çalışan** ' ı seçin.

     Düzenleyici bir XML öğesinin başlangıcını ekler, `<employee` . Bu noktada, öğeye öznitelikler ekleyebilir veya yazarak Başlangıç etiketini kapatabilirsiniz `>` .

5. `>`Etiketi kapatmak için yazın.

6. Düzenleyici bitiş etiketini ekler. Bitiş etiketi, bir doğrulama hatasını gösteren dalgalı alt çizgiyle eklenir. **Araç ipucu** iletiyi görüntüler: **' Employee ' öğesinin içeriği eksik. ' ID ' bekleniyor**.

7. `<`Üye listesinden **ID** yazın ve seçin. Ardından yazın `>` .

     Düzenleyici, XML öğesini ekler `<ID></ID>` ve IMLECI ID başlangıç etiketinden sonra konumlandırır.

8. **ABC** yazın.

     **ABC** metninde dalgalı bir alt çizgi bulunur. **Araç ipucu** iletiyi görüntüler: **' ID ' öğesi, veri türüne göre geçersiz bir değere sahip**.

9. ID öğesine sağ tıklayın ve **Tanıma Git**' i seçin.

     Düzenleyici, *HireDate. xsd* dosyasını yeni bir belge penceresinde açar ve imleci kimlik şeması öğe tanımına konumlandırır.

10. XML dosyasına dönün ve **ABC** metnini **123** ile değiştirin.

     Dalgalı alt çizgi ve **araç Ipucu** ID öğesi değeri altında temizlenir. Çalışan bitiş etiketi için **araç ipucu** artık iletiyi görüntülüyor: **' Employee ' öğesinin içeriği eksik. ' İşe alma tarihi ' bekleniyor**.

11. İmleci ID End etiketinden sonra yerleştirin, yazın `<` , üye listesinden **işe alma tarihi** ' ni seçin ve ardından yazın `>` .

     Düzenleyici, XML öğesini ekler `<hire-date></hire-date>` ve sonra, işe alma tarihi başlangıç etiketinden sonra imleci konumlandırır.

12. İşe alma tarihi değeri için **2003-01-10** yazın.

## <a name="to-format-the-xml-document"></a>XML belgesini biçimlendirmek için

- XML Düzenleyicisi araç çubuğunda **belge Biçimlendir** düğmesini seçin veya **CTRL** + **E**,**D**' ye basın.

   ![Visual Studio XML belgesi düğmesini Biçimlendir](media/format-xml-document.png)

   XML belgesi yeniden biçimlendirilir.

## <a name="to-save-the-xml-document"></a>XML belgesini kaydetmek için

1. **Dosya** menüsündeki **Farklı Kaydet** seçeneğini belirleyin.

     **Dosyayı farklı kaydet** iletişim kutusu görüntülenir. Varsayılan dosya adı *' XMLFile1 '*.

2. XML belgesi için dosya adı ve konum girin ve **Kaydet**' e tıklayın.

## <a name="hiredatexsd-file"></a>hireDate. xsd dosyası

Bu kılavuzda aşağıdaki şema dosyası kullanılır:

```xml
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Ayrıca bkz.

- [XML düzenleyicisi](../xml-tools/xml-editor.md)

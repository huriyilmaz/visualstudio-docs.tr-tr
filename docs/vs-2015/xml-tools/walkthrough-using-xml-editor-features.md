---
title: 'İzlenecek yol: XML Düzenleyicisi özelliklerini kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa954cfb356593a4f22a44faddd69acdcfc93e37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669563"
---
# <a name="walkthrough-using-xml-editor-features"></a>İzlenecek Yol: XML Düzenleyicisi Özelliklerini Kullanma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bu izlenecek yolda, yeni bir XML belgesi oluşturma adımları gösterilmektedir. İzlenecek yol, XML Düzenleyicisi 'nin XML yazma için değerli hale getirme özelliklerini de kullanır.

> [!NOTE]
> İzlenecek yolu başlatmadan önce, hireDate. xsd dosyasını (Bu konuya aşağıda verilmiştir) yerel bilgisayarınıza kaydedin.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Yeni bir XML dosyası oluşturmak ve bir XML şeması ile ilişkilendirmek için

1. **Dosya** menüsünde, **Yeni**' nin üzerine gelin ve **Dosya**' ya tıklayın.

2. **Şablonlar** bölmesinde **XML dosyası** ' nı seçin ve **Aç**' a tıklayın.

     Düzenleyicide yeni bir dosya açılır. Dosya, `<?xml version="1.0" encoding="utf-8">` varsayılan bir XML bildirimi içerir.

3. Belge Özellikleri penceresinde, **şemalar** alanındaki ( **...** ) düğmesine tıklayın.

     **Xsd şemaları** iletişim kutusu görüntülenir.

4. **Ekle**'yi tıklatın.

     **XSD şeması aç** iletişim kutusu görüntülenir.

5. HireDate. xsd dosyasını seçin ve **Aç**' a tıklayın.

6. **Tamam**'a tıklayın.

     XML şeması artık XML belgesiyle ilişkili. XML şeması belgeyi doğrulamak için kullanılır. IntelliSense tarafından geçerli öğelerin üye listesini doldurmak için de kullanılır.

### <a name="to-add-data"></a>Veri eklemek için

1. Düzenleyici bölmesine `<` yazın.

     Üyeler listesi olası öğeleri görüntüler:

    - yorum eklemek için **!--** .

    - **!** Belge türü eklemek IÇIN DOCTYPE.

    - **?** bir işleme yönergesi eklemek için.

    - kök öğeyi eklemek için **çalışan** .

2. Bir yorum düğümü eklemek için **\<!--** SEÇIN ve ENTER tuşuna basın.

     Düzenleyici bir açıklama sonu etiketi ekler ve imleci başlangıç ve bitiş açıklaması etiketleri arasına yerleştirir.

3. **Test XML dosyasına**yazın.

4. Yeni bir satıra `<` yazın ve üye listesinden **çalışan** ' ı seçin.

     Düzenleyici, bir XML öğesi `<employee` başlangıcını ekler. Bu noktada, öğeye öznitelikler ekleyebilir veya `>` yazarak Başlangıç etiketini kapatabilirsiniz.

5. Etiketi kapatmak için `>` yazın.

6. Düzenleyici bitiş etiketini ekler. Bitiş etiketi, bir doğrulama hatasını gösteren dalgalı alt çizgiyle eklenir. Araç Ipucu iletiyi görüntüler: ' Employee ' öğesinin içeriği eksik. ' ID ' bekleniyor.

7. @No__t_0 yazın ve üye listesinden **kimliği** seçin. @No__t_0 yazın.

     Düzenleyici, XML öğesini ekler, `<ID></ID>` ve imleci ID başlangıç etiketinden sonra konumlandırır.

8. **ABC**yazın.

     **ABC** metninde dalgalı bir alt çizgi bulunur. Araç Ipucu iletiyi görüntüler: ' ID ' öğesi, veri türüne göre geçersiz bir değere sahip.

9. ID öğesine sağ tıklayın ve **Tanıma Git**' i seçin.

     Düzenleyici, hireDate. xsd dosyasını yeni bir belge penceresinde açar ve imleci KIMLIK şeması öğe tanımına konumlandırır.

10. XML dosyasına dönün ve **ABC** metnini **123**ile değiştirin.

     Dalgalı alt çizgi ve araç Ipucu ID öğesi değeri altında temizlenir. Çalışan bitiş etiketi için araç Ipucu artık iletiyi görüntülüyor: ' Employee ' öğesinin içeriği eksik. ' İşe alma tarihi ' bekleniyor.

11. İmleci ID End etiketinden sonra yerleştirin, `<` yazın, üye listesinden işe alma tarihi ' ni seçin ve `>` yazın.

     Düzenleyici, bir XML öğesi ekler, `<hire-date></hire-date>` ve imleci, işe alma tarihi başlangıç etiketinden sonra konumlandırır.

12. İşe alma tarihi değeri için **2003-01-10** yazın.

### <a name="to-format-the-xml-document"></a>XML belgesini biçimlendirmek için

1. XML Düzenleyicisi araç çubuğundan **belge Biçimlendir** düğmesini seçin.

     XML belgesi yeniden biçimlendirilir.

### <a name="to-save-the-xml-document"></a>XML belgesini kaydetmek için

1. **Dosya** menüsünde **farklı kaydet**' i seçin.

     **Dosyayı farklı kaydet** iletişim kutusu görüntülenir. Varsayılan dosya adı ' XMLFile1 '.

2. XML belgesi için dosya adı ve konum girin ve **Kaydet**' e tıklayın.

## <a name="hiredatexsd-file"></a>hireDate. xsd dosyası
 Aşağıdaki şema dosyası, izlenecek yol tarafından kullanılır.

```
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

## <a name="see-also"></a>Ayrıca Bkz.
 [XML Düzenleyicisi](../xml-tools/xml-editor.md)

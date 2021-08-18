---
title: 'Adım adım kılavuz: İçerik denetimlerini özel XML bölümlerine bağlama'
description: Belgede depolanan Word to XML verileri için belge düzeyi özelleştirmede içerik denetimlerini bağlamayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- PlainTextContentControl, binding to a custom XML part
- custom XML parts, binding to content controls
- content controls [Office development in Visual Studio], data binding
- data binding [Office development in Visual Studio], content controls
- DropDownListContentControl, binding items to a custom XML part
- DatePickerContentControl, binding to a custom XML part
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 506b919be7a6e84bf6710166e09da4df7d1e7c2d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147719"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>Adım adım kılavuz: İçerik denetimlerini özel XML bölümlerine bağlama
  Bu kılavuzda, belgede depolanan Word to XML verileri için belge düzeyi özelleştirmede içerik denetimlerinin nasıl bağlanacağını gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word, özel XML bölümleri adlı XML *verilerini bir belgede* depolamanızı sağlar. İçerik denetimlerini özel bir XML parçasında öğelere bağarak bu verilerin görüntülemesini kontrol edersiniz. Bu kılavuzda yer alan örnek belge, özel bir XML bölümünde depolanan çalışan bilgilerini görüntüler. Belgeyi açabilirsiniz, içerik denetimleri XML öğelerinin değerlerini görüntüler. İçerik denetimlerde metinde yaptığınız tüm değişiklikler özel XML parçasına kaydedilir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Tasarım zamanında belge düzeyi projesinde Word belgesine içerik denetimleri ekleme.

- bir XML veri dosyası ve içerik denetimlerine bağlanabilecek öğeleri tanımlayan bir XML şeması oluşturma.

- XML şemasını tasarım zamanında belgeye ekleme.

- XML dosyasının içeriğini çalışma zamanında belge içinde özel bir XML parçasına ekleme.

- İçerik denetimlerini özel XML parçasının öğelerine bağlama.

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>BIR'yi XML şemasında tanımlanan bir değer kümesine bağlama.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Yeni bir Word belge projesi oluşturma
 Kılavuzda kullanmak üzere bir Word belgesi oluşturun.

### <a name="to-create-a-new-word-document-project"></a>Yeni bir Word belge projesi oluşturmak için

1. EmployeeControls adıyla bir **Word belgesi projesi oluşturun.** Çözüm için yeni bir belge oluşturun. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]yeni Word belgesini tasarımcıda açar ve **EmployeeControls projesini** **Çözüm Gezgini.**

## <a name="add-content-controls-to-the-document"></a>Belgeye içerik denetimleri ekleme
 Kullanıcının bir çalışanla ilgili bilgileri görüntüleyemez veya düzenleyemez olduğu üç farklı tür içerik denetimi içeren bir tablo oluşturun.

### <a name="to-add-content-controls-to-the-document"></a>Belgeye içerik denetimleri eklemek için

1. Tasarımcıda barındırılan Word [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] belgesinde Şerit'te Ekle sekmesini  seçin.

2. Tablolar **grubunda Tablo'ya** **tıklayın** ve 2 sütun ve 3 satır içeren bir tablo ekleyin.

3. İlk sütuna metin yazarak aşağıdaki sütuna benzer bir metin yazın:

   ||
   |-|
   |**Çalışan Adı**|
   |**İşe Giriş Tarihi**|
   |**Başlık**|

4. Tablonun ikinci sütununda ilk satırı (Çalışan Adı'nın **yanında) seçin.**

5. Şeritte Geliştirici **sekmesini** seçin.

   > [!NOTE]
   > Geliştirici **sekmesi** görünmüyorsa, önce bunu göstermeniz gerekir. Daha fazla bilgi için [şeritteki Geliştirici sekmesini gösterme.](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md)

6. Denetimler **grubunda,** ilk **hücreye** bir eklemek için ![Text düğmesini PlainTextContentControl](../vsto/media/plaintextcontrol.gif "Plaintextcontentcontrol") <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> seçin.

7. Tablonun ikinci sütununda ikinci satırı (İşe Alma Tarihi'nin **yanında) seçin.**

8. Denetimler **grubunda** ![DatePickerContentControl Tarih](../vsto/media/datepicker.gif "Datepickercontentcontrol") Seçici düğmesini seçarak ikinci  <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> hücreye bir ekleyin.

9. Tablonun ikinci sütununda üçüncü satırı (Başlık'ın yanında) **seçin.**

10. Denetimler **grubunda,** son **hücreye** bir eklemek için Açılan Liste düğmesi ![DropDownListContentControl'ı](../vsto/media/dropdownlist.gif "Dropdownlistcontentcontrol") <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> seçin.

    Bu, bu proje için tüm kullanıcı arabirimidir. Projeyi şimdi çalıştırdıysanız ilk satıra metin yazarak ikinci satırda bir tarih seçin. Sonraki adım, belgeye görüntülemek istediğiniz verileri bir XML dosyasında eklemektir.

## <a name="create-the-xml-data-file"></a>XML veri dosyasını oluşturma
 Genellikle, bir dosya veya veritabanı gibi bir dış kaynaktan özel bir XML bölümünde depolamak üzere XML verileri alırsınız. Bu kılavuzda, çalışan verilerini içeren ve belgede içerik denetimlerine bağlayacağınız öğelerle işaretlenmiş bir XML dosyası oluşturabilirsiniz. Verileri çalışma zamanında kullanılabilir yapmak için XML dosyasını özelleştirme derlemesinde kaynak olarak ekleme.

#### <a name="to-create-the-data-file"></a>Veri dosyasını oluşturmak için

1. Yeni **Project** Ekle'yi **seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Şablonlar **bölmesinde** **XML Dosyası'ı seçin.**

3. Dosyaya **employees.xml** ve ardından Ekle **düğmesini** seçin.

     employees.xml dosyası Kod Düzenleyicisi'nde açılır.

4. **employees.xml** içeriğini aşağıdaki metinle değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <employees xmlns="http://schemas.microsoft.com/vsto/samples">
      <employee>
        <name>Karina Leal</name>
        <hireDate>1999-04-01</hireDate>
        <title>Manager</title>
      </employee>
    </employees>
    ```

5. Bu **Çözüm Gezgini,** **dosyanınemployees.xml** seçin.

6. Özellikler **penceresinde** Derleme Eylemi özelliğini **seçin** ve değeri Katıştırılmış Kaynak **olarak değiştirin.**

     Bu adım, projeyi derlemek için XML dosyasını derlemeye kaynak olarak katıştırır. Bu, çalışma zamanında XML dosyasının içeriğine erişmeye olanak sağlar.

## <a name="create-an-xml-schema"></a>XML Şeması Oluşturma
 İçerik denetiminizi özel XML parçasında tek bir öğeye bağlamak için XML şemasını kullanmak zorunda değildir. Ancak, bir değer kümesine bağlamak için, daha önce oluşturduğunuz XML veri dosyasını doğrulayan bir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> XML şeması oluşturmanız gerekir. XML şeması, öğesi için olası değerleri `title` tanımlar. Bu kılavuzda <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> daha sonra öğesini bu öğeye bağlayabilirsiniz.

#### <a name="to-create-an-xml-schema"></a>XML şeması oluşturmak için

1. Yeni **Project** Ekle'yi **seçin.**

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. Şablonlar **bölmesinde** **XML Şeması'ı seçin.**

3. Şemaya **employees.xsd adını** girin ve Ekle **düğmesini** seçin.

     Şema tasarımcısı açılır.

4. Bu **Çözüm Gezgini** **employees.xsd** kısayol menüsünü açın ve ardından Kodu Görüntüle'yi **seçin.**

5. **employees.xsd dosyasının içeriğini** aşağıdaki şemayla değiştirin.

    ```xml
    <?xml version="1.0" encoding="utf-8" ?>
    <xs:schema xmlns="http://schemas.microsoft.com/vsto/samples"
        targetNamespace="http://schemas.microsoft.com/vsto/samples"
        xmlns:xs="http://www.w3.org/2001/XMLSchema"
        elementFormDefault="qualified">
      <xs:element name="employees" type="EmployeesType"></xs:element>
      <xs:complexType name="EmployeesType">
        <xs:all>
          <xs:element name="employee" type="EmployeeType"/>
        </xs:all>
      </xs:complexType>
      <xs:complexType name="EmployeeType">
        <xs:sequence>
          <xs:element name="name" type="xs:string" minOccurs="1" maxOccurs="1"/>
          <xs:element name="hireDate" type="xs:date" minOccurs="1" maxOccurs="1"/>
          <xs:element name="title" type="TitleType" minOccurs="1" maxOccurs="1"/>
        </xs:sequence>
      </xs:complexType>
      <xs:simpleType name="TitleType">
        <xs:restriction base="xs:string">
          <xs:enumeration value ="Engineer"/>
          <xs:enumeration value ="Designer"/>
          <xs:enumeration value ="Manager"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:schema>
    ```

6. Dosya **menüsünde,** **değişikliklerinizi** **employees.xmlve employees.xsd** dosyalarına kaydetmek için Hepsini Kaydet'e tıklayın. 

## <a name="attach-the-xml-schema-to-the-document"></a>XML şemasını belgeye ekleme
 öğesinin geçerli değerlerine bağlamak için XML <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> şemasını belgeye `title` ekleyebilirsiniz.

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>XML şemasını belgeye eklemek için ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Tasarımcıda **EmployeeControls.docx** etkinleştirme.

2. Şerit'te Geliştirici **sekmesini** ve ardından Eklentiler **düğmesini** seçin.

3. Şablonlar **ve Eklentiler iletişim kutusunda** **XML** Şeması sekmesini ve ardından Şema Ekle **düğmesini** seçin.

4. Proje **dizininizin içinde bulunan employees.xsd** şemasına göz atarak Aç **düğmesini** seçin.

5. Şema **Ayarları** iletişim kutusunda **Tamam Ayarlar** seçin.

6. Şablonlar **ve** Eklentiler iletişim **kutusunu kapatmak için Tamam düğmesini** seçin.

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>XML şemasını belgeye eklemek için (Word 2010)

1. Tasarımcıda **EmployeeControls.docx** etkinleştirme.

2. Şeritte Geliştirici **sekmesini** seçin.

3. XML **grubunda** Şema **düğmesini** seçin.

4. Şablonlar **ve Eklentiler iletişim kutusunda** **XML** Şeması sekmesini ve ardından Şema Ekle **düğmesini** seçin.

5. Proje **dizininizin içinde bulunan employees.xsd** şemasına göz atarak Aç **düğmesini** seçin.

6. Şema **Ayarları** iletişim kutusunda **Tamam Ayarlar** seçin.

7. Şablonlar **ve** Eklentiler iletişim **kutusunu kapatmak için Tamam düğmesini** seçin.

     **XML Yapısı görev** bölmesi açılır.

8. XML Yapısı **görev** bölmesini kapatın.

## <a name="add-a-custom-xml-part-to-the-document"></a>Belgeye özel XML bölümü ekleme
 İçerik denetimlerini XML dosyasındaki öğelere bağlamadan önce XML dosyasının içeriğini belgede yeni bir özel XML parçasına eklemeniz gerekir.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Belgeye özel bir XML bölümü eklemek için

1. Bu **Çözüm Gezgini** **ThisDocument.cs veya ThisDocument.vb** kısayol menüsünü **açın** ve Ardından Kodu Görüntüle'yi **seçin.**

2. Aşağıdaki bildirimleri sınıfına `ThisDocument` ekleyin. Bu kod, belgeye özel bir XML bölümü eklemek için kullanabileceğiniz birkaç nesne bildirecek.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet1":::

3. Sınıfına aşağıdaki yöntemi `ThisDocument` ekleyin. Bu yöntem, derlemeye kaynak olarak eklenmiş XML veri dosyasının içeriğini alır ve içeriği bir XML dizesi olarak döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet3":::

4. Sınıfına aşağıdaki yöntemi `ThisDocument` ekleyin. yöntemi, `AddCustomXmlPart` yöntemine geçirilen bir XML dizesi içeren yeni bir özel XML bölümü oluşturur.

     Özel XML parçasının yalnızca bir kez oluşturulduktan emin olmak için yöntemi, özel XML bölümünü yalnızca eşleşen GUID içeren bir özel XML bölümü belgede mevcut yoksa oluşturur. Bu yöntem ilk kez çağrıldı mı, özelliğin değerini <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> dizeye `employeeXMLPartID` kaydeder. Dizenin `employeeXMLPartID` değeri, özniteliği kullanılarak bildirilene kadar belgede kalıcı <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> olur.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet4":::

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>İçerik denetimlerini özel XML parçasının öğelerine bağlama
 Her içerik denetimi **xmlMapping** özelliğini kullanarak her içerik denetimi özel XML parçasında bir öğeye bağlayın.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>İçerik denetimlerini özel XML parçasının öğelerine bağlamak için

1. Sınıfına aşağıdaki yöntemi `ThisDocument` ekleyin. Bu yöntem, her içerik denetimlerini özel XML parçasında bir öğeye bağlar ve öğesinin tarih görüntüleme biçimini <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> ayarlar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet5":::

## <a name="run-your-code-when-the-document-is-opened"></a>Belge açıldığında kodunuzu çalıştırma
 Özel XML bölümünü oluşturun ve özel denetimleri belge açıldığında verilere bağlayın.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Belge açıldığında kodunuzu çalıştırmak için

1. Aşağıdaki kodu sınıfının `ThisDocument_Startup` yöntemine `ThisDocument` ekleyin. Bu kod xml dizesini **employees.xml** dosyasından alır, XML dizesini belgede yeni bir özel XML parçasına ekler ve içerik denetimlerini özel XML parçasındaki öğelere bağlar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet2":::

## <a name="test-the-project"></a>Projeyi test etme
 Belgeyi açıkken, içerik denetimleri özel XML bölümünde yer alan öğelerden verileri görüntüler. öğesine <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> tıklar ve öğesi için `title` **employees.xsd** dosyasında tanımlanan üç geçerli değerden birini seçin. İçerik denetimlerinin herhangi bir bölümünde verileri düzenlersiniz, yeni değerler belgenin özel XML parçasına kaydedilir.

### <a name="to-test-the-content-controls"></a>İçerik denetimlerini test etmek için

1. Projeyi **çalıştırmak için F5** tuşuna basın.

2. Belgede yer alan tablonun aşağıdaki tabloya benzer olduğunu doğrulayın. İkinci sütundaki dizelerin her biri, belgedeki özel XML bölümünde yer alan bir öğeden elde edilir.

    |Sütun|Değer|
    |-|-|
    |**Çalışan Adı**|**Karina Leal**|
    |**İşe Giriş Tarihi**|**1 Nisan 1999**|
    |**Başlık**|**Yönetici**|

3. Çalışan Adı hücresi'nin sağ **tarafından hücreyi seçin** ve farklı bir ad yazın.

4. İşe Alma Tarihi hücresi'nin **sağ tarafından hücreyi** seçin ve tarih seçicide farklı bir tarih seçin.

5. Başlık hücresi'nin sağ **tarafından hücreyi** seçin ve açılan listeden yeni bir öğe seçin.

6. Belgeyi kaydedin ve kapatın.

7. Bu Dosya Gezgini projenizin *konumu altındaki \bin\Debug* klasörünü açın.

8. Dosyanın kısayol menüsünü açın **EmployeeControls.docx** yeniden adlandır'ı **seçin.**

9. Dosyayı olarak **EmployeeControls.docx.zip.**

     Bu **EmployeeControls.docx** Açık XML Biçiminde kaydedilir. Bu belgeyi dosya adı *uzantısıyla.zip,* belgenin içeriğini inceebilirsiniz. Open XML hakkında daha fazla bilgi için, Office [(2007) Open XML](/previous-versions/office/developer/office-2007/aa338205(v=office.12))dosya biçimlerini tanıtma teknik makalesine bakın.

10. EmployeeControls.docx.zip **açın.**

11. **customXml klasörünü** açın.

12. Dosyanın kısayol menüsünü **açınitem2.xml'yi** **seçin.**

     Bu dosya, belgeye ekley istediğiniz özel XML bölümünü içerir.

13. `name`, ve `hireDate` öğelerinin `title` belgede içerik denetimlerine girdiğiniz yeni değerleri içerdiğini doğrulayın.

14. Dosyanın **item2.xml** kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 İçerik denetimlerini kullanma hakkında daha fazla bilgi edinmek için şu konu başlıklarını kullanabilirsiniz:

- Şablon oluşturmak için tüm kullanılabilir içerik denetimlerini kullanın. Daha fazla bilgi için [bkz. Kılavuz: İçerik denetimlerini kullanarak şablon oluşturma.](../vsto/walkthrough-creating-a-template-by-using-content-controls.md)

- Belge kapatılırken özel XML parçalarında verileri değiştirme. Kullanıcı belgeyi bir daha açtığında, XML öğelerine bağlı içerik denetimleri yeni verileri görüntüler.

- Bir belgenin bölümlerini korumak için içerik denetimlerini kullanın. Daha fazla bilgi için, [bkz. How to: Protect parts of documents by using content controls](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word'i otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Nasıl kullanılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Nasıl kullanılır: İçerik denetimlerini kullanarak belgelerin bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Konak öğelerine ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlı sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Çalışma zamanında Office denetimler ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)

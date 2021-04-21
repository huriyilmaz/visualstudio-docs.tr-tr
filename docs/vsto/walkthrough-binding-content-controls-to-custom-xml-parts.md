---
title: 'İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama'
description: Word için belge düzeyi özelleştirmesindeki içerik denetimlerini belgede depolanan XML verilerine bağlamayı öğrenin.
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
ms.workload:
- office
ms.openlocfilehash: 6e4a10949f463cc769890b828ba39de30a9b4c1c
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107824581"
---
# <a name="walkthrough-bind-content-controls-to-custom-xml-parts"></a>İzlenecek yol: içerik denetimlerini özel XML bölümlerine bağlama
  Bu izlenecek yol, Word için belge düzeyi özelleştirmesindeki içerik denetimlerini belgede depolanan XML verilerine nasıl bağlayabileceğinizi gösterir.

 [!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

 Word, bir belgede *özel XML parçaları* olarak adlandırılan XML verilerini depolamanıza olanak sağlar. İçerik denetimlerini özel bir XML parçasındaki öğelere bağlayarak bu verilerin görüntülenmesini denetleyebilirsiniz. Bu izlenecek yolda örnek belge, özel bir XML bölümünde depolanan çalışan bilgilerini görüntüler. Belgeyi açtığınızda, içerik denetimleri XML öğelerinin değerlerini görüntüler. İçerik denetimlerindeki metinde yaptığınız tüm değişiklikler özel XML bölümüne kaydedilir.

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Belge düzeyi projesindeki Word belgesine içerik denetimleri ekleme tasarım zamanı.

- XML veri dosyası ve içerik denetimlerine bağlanacak öğeleri tanımlayan bir XML şeması oluşturma.

- XML şemasını belgeye tasarım zamanında ekleme.

- XML dosyasının içeriğini çalışma zamanında belgedeki özel bir XML bölümüne ekleme.

- İçerik denetimlerini özel XML parçasındaki öğelere bağlama.

- <xref:Microsoft.Office.Tools.Word.DropDownListContentControl>XML şemasında tanımlanmış bir değerler kümesine bağlama.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- Microsoft Word.

## <a name="create-a-new-word-document-project"></a>Yeni bir Word belgesi projesi oluştur
 Yönergede kullanacağınız bir Word belgesi oluşturun.

### <a name="to-create-a-new-word-document-project"></a>Yeni bir Word belgesi projesi oluşturmak için

1. **EmployeeControls** adlı bir Word belgesi projesi oluşturun. Çözüm için yeni bir belge oluşturun. Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] tasarımcıda yeni Word belgesini açar ve **EmployeeControls** projesini **Çözüm Gezgini** ekler.

## <a name="add-content-controls-to-the-document"></a>Belgeye içerik denetimleri ekleme
 Kullanıcının bir çalışanla ilgili bilgileri görüntüleyebileceği veya düzenleyebileceği üç farklı türde içerik denetimi içeren bir tablo oluşturun.

### <a name="to-add-content-controls-to-the-document"></a>Belgeye içerik denetimleri eklemek için

1. Tasarımcıda barındırılan Word belgesinde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] , şeritte **Ekle** sekmesini seçin.

2. **Tablolar** grubunda **tablo**' yı seçin ve 2 sütun ve 3 satır içeren bir tablo ekleyin.

3. Aşağıdaki sütuna benzer olacak şekilde ilk sütuna metin yazın:

   ||
   |-|
   |**Çalışan adı**|
   |**İşe Giriş Tarihi**|
   |**Başlık**|

4. Tablonun ikinci sütununda, ilk satırı ( **çalışan adı**' nın yanında) seçin.

5. Şeritte **Geliştirici** sekmesini seçin.

   > [!NOTE]
   > **Geliştirici** sekmesi görünür değilse, önce onu göstermelisiniz. Daha fazla bilgi için bkz. [nasıl yapılır: Şeritte Geliştirici sekmesini gösterme](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).

6. **Denetimler** grubunda, ilk hücreye bir eklemek Için ![PlainTextContentControl](../vsto/media/plaintextcontrol.gif "PlainTextContentControl") **metin** düğmesini seçin <xref:Microsoft.Office.Tools.Word.PlainTextContentControl> .

7. Tablonun ikinci sütununda, ikinci satırı ( **işe giriş tarihi**' nin yanında) seçin.

8. **Denetimler** grubunda, ikinci hücreye eklemek Için **Tarih Seçici** düğmesini ![DatePickerContentControl](../vsto/media/datepicker.gif "DatePickerContentControl") ' i seçin <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> .

9. Tablonun ikinci sütununda, üçüncü satırı ( **başlık**' ın yanında) seçin.

10. **Denetimler** grubunda, son hücreye eklemek Için aşağı **açılan liste** düğmesini ![DropDownListContentControl](../vsto/media/dropdownlist.gif "DropDownListContentControl") ' ı seçin <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> .

    Bu proje için Kullanıcı arabiriminin tamamı budur. Projeyi Şimdi çalıştırırsanız, ilk satıra metin yazabilir ve ikinci satırdaki bir tarihi seçebilirsiniz. Bir sonraki adım, göstermek istediğiniz verileri bir XML dosyasındaki belgeye eklemektir.

## <a name="create-the-xml-data-file"></a>XML veri dosyası oluşturma
 Genellikle, bir dosya veya veritabanı gibi bir dış kaynaktan özel bir XML bölümünde depolanacak XML verilerini elde edersiniz. Bu kılavuzda, belgedeki içerik denetimlerine bağlayacağınız öğeler tarafından işaretlenen çalışan verilerini içeren bir XML dosyası oluşturacaksınız. Verileri çalışma zamanında kullanılabilir hale getirmek için, XML dosyasını özelleştirme derlemesine bir kaynak olarak ekleyin.

#### <a name="to-create-the-data-file"></a>Veri dosyası oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. **Şablonlar** bölmesinde **XML dosyası**' nı seçin.

3. **employees.xml** dosyayı adlandırın ve ardından **Ekle** düğmesini seçin.

     **employees.xml** dosyası kod düzenleyicisinde açılır.

4. **employees.xml** dosyasının içeriğini aşağıdaki metinle değiştirin.

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

5. **Çözüm Gezgini** **employees.xml** dosyasını seçin.

6. **Özellikler** penceresinde **derleme eylemi** özelliğini seçin ve ardından değeri **gömülü kaynak** olarak değiştirin.

     Bu adım, projeyi derlediğinizde XML dosyasını derlemeye bir kaynak olarak katıştırır. Bu, çalışma zamanında XML dosyasının içeriğine erişmenizi sağlar.

## <a name="create-an-xml-schema"></a>XML şeması oluşturma
 Bir içerik denetimini özel bir XML bölümünde tek bir öğeye bağlamak istiyorsanız, bir XML şeması kullanmak zorunda değilsiniz. Ancak, öğesini <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> bir değer kümesine bağlamak için, daha önce oluşturduğunuz XML veri dosyasını doğrulayan BIR XML Şeması oluşturmanız gerekir. XML şeması, öğesi için olası değerleri tanımlar `title` . Bu <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> öğeyi daha sonra Bu izlenecek yolda bağlayacaksınız.

#### <a name="to-create-an-xml-schema"></a>Bir XML şeması oluşturmak için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

     **Yeni Öğe Ekle** iletişim kutusu görünür.

2. **Şablonlar** bölmesinde, **XML şeması**' nı seçin.

3. Şemayı **employees. xsd** olarak adlandırın ve **Ekle** düğmesini seçin.

     Şema Tasarımcısı açılır.

4. **Çözüm Gezgini**, **employees. xsd** için kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

5. **Employees. xsd** dosyasının içeriğini aşağıdaki şema ile değiştirin.

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

6. Değişikliklerinizi **employees.xml** ve **employees. xsd** dosyalarını kaydetmek Için **Dosya** menüsünde **Tümünü Kaydet** ' e tıklayın.

## <a name="attach-the-xml-schema-to-the-document"></a>XML şemasını belgeye iliştirme
 XML şemasını, öğesinin geçerli değerlerine bağlamak için belgeye iliştirmelidir <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> `title` .

### <a name="to-attach-the-xml-schema-to-the-document--word_15_short"></a>XML şemasını belgeye eklemek için ( [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] )

1. Tasarımcıda **EmployeeControls.docx** etkinleştirin.

2. Şeritte **Geliştirici** sekmesini seçin ve ardından **Eklentiler düğmesini seçin** .

3. **Şablonlar ve eklentiler** iletişim kutusunda, **XML şeması** sekmesini seçin ve ardından **şema ekle** düğmesini seçin.

4. Daha önce oluşturduğunuz, proje dizininizde bulunan **employees. xsd** şemasına gidin ve sonra **Aç** düğmesini seçin.

5. **Şema ayarları** Iletişim kutusunda **Tamam** düğmesini seçin.

6. **Şablonlar ve eklentiler** iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

### <a name="to-attach-the-xml-schema-to-the-document-word-2010"></a>XML şemasını belgeye eklemek için (Word 2010)

1. Tasarımcıda **EmployeeControls.docx** etkinleştirin.

2. Şeritte **Geliştirici** sekmesini seçin.

3. **XML** grubunda **şema** düğmesini seçin.

4. **Şablonlar ve eklentiler** iletişim kutusunda, **XML şeması** sekmesini seçin ve ardından **şema ekle** düğmesini seçin.

5. Daha önce oluşturduğunuz ve proje dizininizde bulunan **employees. xsd** şemasına gidin ve **Aç** düğmesini seçin.

6. **Şema ayarları** Iletişim kutusunda **Tamam** düğmesini seçin.

7. **Şablonlar ve eklentiler** iletişim kutusunu kapatmak için **Tamam** düğmesini seçin.

     **XML yapısı** görev bölmesi açılır.

8. **XML yapısı** görev bölmesini kapatın.

## <a name="add-a-custom-xml-part-to-the-document"></a>Belgeye özel bir XML bölümü ekleme
 İçerik denetimlerini XML dosyasındaki öğelere bağlayabilmeniz için önce, XML dosyasının içeriğini belgedeki yeni bir özel XML bölümüne eklemeniz gerekir.

### <a name="to-add-a-custom-xml-part-to-the-document"></a>Belgeye özel bir XML bölümü eklemek için

1. **Çözüm Gezgini**' de, **ThisDocument. cs** veya **ThisDocument. vb** kısayol menüsünü açın ve **kodu görüntüle**' yi seçin.

2. Sınıfına aşağıdaki bildirimleri ekleyin `ThisDocument` . Bu kod, belgeye özel bir XML bölümü eklemek için kullanacağınız birkaç nesne bildirir.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet1":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet1":::

3. Sınıfına aşağıdaki yöntemi ekleyin `ThisDocument` . Bu yöntem, derlemede bir kaynak olarak katıştırılmış XML veri dosyasının içeriğini alır ve içeriği bir XML dizesi olarak döndürür.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet3":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet3":::

4. Sınıfına aşağıdaki yöntemi ekleyin `ThisDocument` . `AddCustomXmlPart`Yöntemi yöntemine geçirilen BIR XML dizesi içeren yeni bir özel XML bölümü oluşturur.

     Özel XML bölümünün yalnızca bir kez oluşturulduğundan emin olmak için, yöntem yalnızca belgede eşleşen bir GUID 'e sahip özel bir XML bölümü yoksa özel XML bölümünü oluşturur. Bu yöntem ilk kez çağrıldığında, <xref:Microsoft.Office.Core._CustomXMLPart.Id%2A> özelliğinin değerini `employeeXMLPartID` dizeye kaydeder. Dize değeri, `employeeXMLPartID` özniteliği kullanılarak bildirildiği için belgede kalıcı hale getirilir <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet4":::

## <a name="bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>İçerik denetimlerini özel XML bölümünde öğelere bağlama
 Her içerik denetiminin **XmlMapping** özelliğini kullanarak her içerik DENETIMINI özel XML parçasındaki bir öğeye bağlayın.

### <a name="to-bind-the-content-controls-to-elements-in-the-custom-xml-part"></a>İçerik denetimlerini özel XML bölümünde öğelere bağlamak için

1. Sınıfına aşağıdaki yöntemi ekleyin `ThisDocument` . Bu yöntem, her içerik denetimini özel XML parçasındaki bir öğeye bağlar ve öğesinin tarih görüntüleme biçimini ayarlar <xref:Microsoft.Office.Tools.Word.DatePickerContentControl> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet5":::

## <a name="run-your-code-when-the-document-is-opened"></a>Belge açıldığında kodunuzu çalıştırın
 Özel XML bölümünü oluşturun ve belge açıldığında özel denetimleri verilere bağlayın.

### <a name="to-run-your-code-when-the-document-is-opened"></a>Belge açıldığında kodunuzu çalıştırmak için

1. Aşağıdaki kodu `ThisDocument_Startup` sınıfının yöntemine ekleyin `ThisDocument` . Bu kod, **employees.xml** dosyasından XML dizesini alır, XML dizesini belgedeki yeni BIR özel XML bölümüne ekler ve içerik DENETIMLERINI özel XML bölümünde yer alan öğelere bağlar.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/EmployeeControls/ThisDocument.cs" id="Snippet2":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/EmployeeControls/ThisDocument.vb" id="Snippet2":::

## <a name="test-the-project"></a>Projeyi test etme
 Belgeyi açtığınızda, içerik denetimleri özel XML parçasındaki öğelerden verileri görüntüler. <xref:Microsoft.Office.Tools.Word.DropDownListContentControl> `title` **Employees. xsd** dosyasında tanımlanan, öğesi için geçerli üç değerden birini seçmek için öğesine tıklayabilirsiniz. İçerik denetimlerindeki verileri düzenlerseniz, yeni değerler belgedeki özel XML bölümüne kaydedilir.

### <a name="to-test-the-content-controls"></a>İçerik denetimlerini test etmek için

1. Projeyi çalıştırmak için **F5** tuşuna basın.

2. Belgedeki tablonun aşağıdaki tabloya benzediğini doğrulayın. İkinci sütundaki dizelerin her biri belgedeki özel XML bölümündeki bir öğeden elde edilir.

    |Sütun|Değer|
    |-|-|
    |**Çalışan adı**|**Karina Taal**|
    |**İşe Giriş Tarihi**|**1 Nisan 1999**|
    |**Başlık**|**Yönetici**|

3. **Çalışan adı** hücresinin sağ tarafındaki hücreyi seçin ve farklı bir ad yazın.

4. **Işe alma tarihi** hücresinin sağ tarafındaki hücreyi seçin ve tarih seçicide farklı bir tarih seçin.

5. **Başlık** hücresinin sağ tarafındaki hücreyi seçin ve açılan listeden yeni bir öğe seçin.

6. Belgeyi kaydedin ve kapatın.

7. Dosya Gezgini 'nde, projenizin konumu altındaki *\Bin\debug* klasörünü açın.

8. **EmployeeControls.docx** için kısayol menüsünü açın ve **Yeniden Adlandır**' ı seçin.

9. Dosyayı **EmployeeControls.docx.zip** olarak adlandırın.

     **EmployeeControls.docx** belge Open XML biçiminde kaydedilir. Bu belgeyi *. zip* dosya adı uzantısıyla yeniden adlandırarak belgenin içeriğini inceleyebilirsiniz. Open XML hakkında daha fazla bilgi için bkz. [Office (2007) Open XML dosya biçimlerini tanıtma](/previous-versions/office/developer/office-2007/aa338205(v=office.12))teknik makalesi.

10. **EmployeeControls.docx.zip** dosyasını açın.

11. **CustomXml** klasörünü açın.

12. **item2.xml** için kısayol menüsünü açın ve **Aç**' ı seçin.

     Bu dosya, belgeye eklediğiniz özel XML bölümünü içerir.

13. `name`, `hireDate` Ve `title` öğelerinin belgedeki içerik denetimlerine girdiğiniz yeni değerleri içerdiğini doğrulayın.

14. **item2.xml** dosyasını kapatın.

## <a name="next-steps"></a>Sonraki adımlar
 Aşağıdaki konulardan içerik denetimlerini kullanma hakkında daha fazla bilgi edinebilirsiniz:

- Bir şablon oluşturmak için tüm kullanılabilir içerik denetimlerini kullanın. Daha fazla bilgi için bkz. [Izlenecek yol: içerik denetimlerini kullanarak şablon oluşturma](../vsto/walkthrough-creating-a-template-by-using-content-controls.md).

- Belge kapalıyken özel XML bölümlerinde verileri değiştirin. Kullanıcının belgeyi bir sonraki açışında, XML öğelerine bağlanan içerik denetimleri yeni verileri görüntüler.

- Belge parçalarını korumak için içerik denetimlerini kullanın. Daha fazla bilgi için bkz. [nasıl yapılır: içerik denetimlerini kullanarak belge bölümlerini koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Genişletilmiş nesneleri kullanarak Word 'Ü otomatikleştirme](../vsto/automating-word-by-using-extended-objects.md)
- [İçerik denetimleri](../vsto/content-controls.md)
- [Nasıl yapılır: Word belgelerine içerik denetimleri ekleme](../vsto/how-to-add-content-controls-to-word-documents.md)
- [Nasıl yapılır: içerik denetimlerini kullanarak belge parçalarını koruma](../vsto/how-to-protect-parts-of-documents-by-using-content-controls.md)
- [Konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md)
- [Konak öğelerinin ve konak denetimlerinin programlama sınırlamaları](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)
- [Çalışma zamanında Office belgelerine denetim ekleme](../vsto/adding-controls-to-office-documents-at-run-time.md)

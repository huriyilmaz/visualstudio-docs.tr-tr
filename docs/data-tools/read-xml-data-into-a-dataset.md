---
title: Bir veri kümesinin içine XML verileri okuma
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- reading XML
- data access [Visual Studio], XML data
- reading files, XML
- data [Visual Studio], reading from XML files
- reading data, XML files
- XML [Visual Studio], reading
- XML documents, reading
- datasets [Visual Basic], reading XML data
ms.assetid: fae72958-0893-47d6-b3dd-9d42418418e4
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 6dec7cad50d818d4b2418442d8196cb8b5ff046a
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72641369"
---
# <a name="read-xml-data-into-a-dataset"></a>Bir veri kümesinin içine XML verileri okuma

ADO.NET XML verileriyle çalışmak için basit yöntemler sağlar. Bu kılavuzda, XML verilerini bir veri kümesine yükleyen bir Windows uygulaması oluşturacaksınız. Veri kümesi daha sonra bir <xref:System.Windows.Forms.DataGridView> denetiminde görüntülenir. Son olarak, XML dosyasının içeriğini temel alan bir XML şeması metin kutusunda görüntülenir.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma

Ya da C# Visual Basic için yeni bir **Windows Forms uygulama** projesi oluşturun. Projeyi **ReadingXML**olarak adlandırın.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Veri kümesine okunacak XML dosyasını oluştur

Bu izlenecek yol, XML verilerinin bir veri kümesine okunmasına odaklandığı için, bir XML dosyasının içeriği sağlanır.

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

2. **XML dosyası**' nı seçin, dosyayı **yazarlar. xml**olarak adlandırın ve **Ekle**' yi seçin.

   XML dosyası tasarımcıya yüklenir ve düzenleme için hazırlayın.

3. Aşağıdaki XML verilerini, XML bildiriminin altındaki düzenleyiciye yapıştırın:

   ```xml
   <Authors_Table>
     <authors>
       <au_id>172-32-1176</au_id>
       <au_lname>White</au_lname>
       <au_fname>Johnson</au_fname>
       <phone>408 496-7223</phone>
       <address>10932 Bigge Rd.</address>
       <city>Menlo Park</city>
       <state>CA</state>
       <zip>94025</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>213-46-8915</au_id>
       <au_lname>Green</au_lname>
       <au_fname>Margie</au_fname>
       <phone>415 986-7020</phone>
       <address>309 63rd St. #411</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94618</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>238-95-7766</au_id>
       <au_lname>Carson</au_lname>
       <au_fname>Cheryl</au_fname>
       <phone>415 548-7723</phone>
       <address>589 Darwin Ln.</address>
       <city>Berkeley</city>
       <state>CA</state>
       <zip>94705</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>267-41-2394</au_id>
       <au_lname>Hunter</au_lname>
       <au_fname>Anne</au_fname>
       <phone>408 286-2428</phone>
       <address>22 Cleveland Av. #14</address>
       <city>San Jose</city>
       <state>CA</state>
       <zip>95128</zip>
       <contract>true</contract>
     </authors>
     <authors>
       <au_id>274-80-9391</au_id>
       <au_lname>Straight</au_lname>
       <au_fname>Dean</au_fname>
       <phone>415 834-2919</phone>
       <address>5420 College Av.</address>
       <city>Oakland</city>
       <state>CA</state>
       <zip>94609</zip>
       <contract>true</contract>
     </authors>
   </Authors_Table>
   ```

4. **Dosya** menüsünde, **yazarları. xml dosyasını Kaydet**' i seçin.

## <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma

Bu uygulama için Kullanıcı arabirimi aşağıdakilerden oluşur:

- XML dosyasının içeriğini veri olarak görüntüleyen bir <xref:System.Windows.Forms.DataGridView> denetimi.

- XML dosyası için XML şemasını görüntüleyen bir <xref:System.Windows.Forms.TextBox> denetimi.

- İki <xref:System.Windows.Forms.Button> denetimi.

  - Bir düğme, XML dosyasını veri kümesine okur ve <xref:System.Windows.Forms.DataGridView> denetiminde görüntüler.

  - İkinci bir düğme, şemayı veri kümesinden ayıklar ve bir <xref:System.IO.StringWriter> aracılığıyla <xref:System.Windows.Forms.TextBox> denetiminde görüntüler.

### <a name="to-add-controls-to-the-form"></a>Forma denetim eklemek için

1. @No__t_0 Tasarım görünümünde açın.

2. **Araç kutusundan**aşağıdaki denetimleri form üzerine sürükleyin:

    - Bir <xref:System.Windows.Forms.DataGridView> denetimi

    - Bir <xref:System.Windows.Forms.TextBox> denetimi

    - İki <xref:System.Windows.Forms.Button> denetimi

3. Aşağıdaki özellikleri ayarlayın:

    |Denetim|Özellik|Ayar|
    |-------------|--------------|-------------|
    |`TextBox1`|**Çok satırlı**|`true`|
    ||**Çubuklarını**|**Matema**|
    |`Button1`|**Ad**|`ReadXmlButton`|
    ||**Metin**|`Read XML`|
    |`Button2`|**Ad**|`ShowSchemaButton`|
    ||**Metin**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>XML verilerini alan veri kümesini oluşturma

Bu adımda, `authors` adlı yeni bir veri kümesi oluşturursunuz. Veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

1. **Çözüm Gezgini**, **Form1**için kaynak dosyasını seçin ve sonra **Çözüm Gezgini** araç çubuğunda **Tasarımcı görüntüle** düğmesini seçin.

2. [Araç kutusu, veri sekmesinde](../ide/reference/toolbox-data-tab.md)bir **veri kümesini** **Form1**üzerine sürükleyin.

3. **Veri kümesi Ekle** Iletişim kutusunda **türsüz veri kümesi**' ni seçin ve ardından **Tamam**' ı seçin.

     **DataSet1** , bileşen tepsisine eklenir.

4. **Özellikler** penceresinde, `AuthorsDataSet` için **adı** ve <xref:System.Data.DataSet.DataSetName%2A> özelliklerini ayarlayın.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>XML dosyasını veri kümesine okumak için olay işleyicisini oluşturma

**XML oku** düğmesi XML dosyasını veri kümesine okur. Daha sonra, <xref:System.Windows.Forms.DataGridView> denetimindeki özellikleri veri kümesine bağlayan Özellikler belirler.

1. **Çözüm Gezgini**, **Form1**' i seçin ve sonra **Çözüm Gezgini** araç çubuğunda **Tasarımcı görüntüle** düğmesini seçin.

2. **XML oku** düğmesini seçin.

     **Kod düzenleyicisi** `ReadXmlButton_Click` olay işleyicisinde açılır.

3. @No__t_0 olay işleyicisine aşağıdaki kodu yazın:

     [!code-csharp[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_1.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_1.vb)]

4. @No__t_0 olay işleyicisi kodunda, `filepath =` girdisini doğru yola değiştirin.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Metin kutusu içinde şemayı göstermek için olay işleyicisini oluşturma

**Şemayı göster** düğmesi, şemayla doldurulmuş ve <xref:System.Windows.Forms.TextBox>control görüntülenen bir <xref:System.IO.StringWriter> nesnesi oluşturur.

1. **Çözüm Gezgini**, **Form1**' i seçin ve sonra **Tasarımcı görüntüle** düğmesini seçin.

2. **Şemayı göster** düğmesini seçin.

     **Kod düzenleyicisi** `ShowSchemaButton_Click` olay işleyicisinde açılır.

3. Aşağıdaki kodu `ShowSchemaButton_Click` olay işleyicisine yapıştırın.

     [!code-csharp[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/CSharp/read-xml-data-into-a-dataset_2.cs)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../data-tools/codesnippet/VisualBasic/read-xml-data-into-a-dataset_2.vb)]

## <a name="test-the-form"></a>Formu test etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

1. Uygulamayı çalıştırmak için **F5** ' i seçin.

2. **XML oku** düğmesini seçin.

     DataGridView, XML dosyasının içeriğini görüntüler.

3. **Şemayı göster** düğmesini seçin.

     Metin kutusu XML dosyası için XML şemasını görüntüler.

## <a name="next-steps"></a>Sonraki adımlar

Bu izlenecek yol, bir XML dosyasını bir veri kümesine okumayla ilgili temel bilgileri ve XML dosyasının içeriğine göre bir şema oluşturmayı öğretir. Daha sonra gerçekleştirebileceğiniz bazı görevler şunlardır:

- Veri kümesindeki verileri düzenleyin ve XML olarak yeniden yazın. Daha fazla bilgi için bkz. <xref:System.Data.DataSet.WriteXml%2A>.

- Veri kümesindeki verileri düzenleyin ve veritabanına yazın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio 'da XML araçları](../xml-tools/xml-tools-in-visual-studio.md)

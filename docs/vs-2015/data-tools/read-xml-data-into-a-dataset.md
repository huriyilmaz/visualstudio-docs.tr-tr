---
title: XML verilerini bir veri kümesine okuma | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c34fb87c02ff60d9b28c43130d6fbf3a12e70349
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72652897"
---
# <a name="read-xml-data-into-a-dataset"></a>Bir veri kümesinin içine XML verileri okuma
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

ADO.NET XML verileriyle çalışmak için basit yöntemler sağlar. Bu kılavuzda, XML verilerini bir veri kümesine yükleyen bir Windows uygulaması oluşturacaksınız. Veri kümesi daha sonra bir denetimde görüntülenir <xref:System.Windows.Forms.DataGridView> . Son olarak, XML dosyasının içeriğini temel alan bir XML şeması metin kutusunda görüntülenir.

 Bu izlenecek yol beş ana adımdan oluşur:

1. Yeni bir proje oluşturma

2. Veri kümesine okunacak bir XML dosyası oluşturma

3. Kullanıcı arabirimi oluşturma

4. Veri kümesini oluşturma, XML dosyasını okuma ve bir <xref:System.Windows.Forms.DataGridView> denetimde görüntüleme

5. Bir denetimdeki XML dosyasını temel alan XML şemasını göstermek için kod ekleme <xref:System.Windows.Forms.TextBox>

> [!NOTE]
> Gördüğünüz iletişim kutuları ve menü komutları, etkin ayarlarınıza veya kullandığınız sürüme bağlı olarak yardım bölümünde açıklananlardan farklı bir şekilde farklılık gösterebilir. Ayarlarınızı değiştirmek için  **Araçlar** menüsünden**Içeri ve dışarı aktarma ayarları**' nı seçin. Daha fazla bilgi için bkz. [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 Bu adımda, bu yönergeyi içeren bir Visual Basic veya Visual C# projesi oluşturacaksınız.

#### <a name="to-create-the-new-windows-project"></a>Yeni Windows projesi oluşturmak için

1. **Dosya** menüsünde Yeni bir proje oluşturun.

2. Projeyi adlandırın `ReadingXML` .

3. **Windows uygulaması**' nı seçin ve ardından **Tamam**' ı seçin. Daha fazla bilgi için bkz. [Istemci uygulamaları](https://msdn.microsoft.com/library/2dfb50b7-5af2-4e12-9bbb-c5ade0e39a68).

     **ReadingXML** projesi oluşturulup **Çözüm Gezgini**eklenir.

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Veri kümesine okunacak XML dosyasını oluştur
 Bu izlenecek yol, XML verilerinin bir veri kümesine okunmasına odaklandığı için, bir XML dosyasının içeriği sağlanır.

#### <a name="to-create-the-xml-file-that-will-be-read-into-the-dataset"></a>Veri kümesine okunacak XML dosyasını oluşturmak için

1. **Proje** menüsünde**Yeni öğe Ekle**' yi seçin.

2. **XML dosyası**' nı seçin, dosyayı adlandırın `authors.xml` ve ardından **Ekle**' yi seçin.

     XML dosyası tasarımcıya yüklenir ve düzenleme için hazırlayın.

3. Aşağıdaki kodu, XML bildiriminin altındaki düzenleyiciye yapıştırın:

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

4. **Dosya** menüsünde**authors.xmlkaydet **' i seçin.

## <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma
 Bu uygulama için Kullanıcı arabirimi aşağıdakilerden oluşur:

- <xref:System.Windows.Forms.DataGridView>XML dosyasının içeriğini veri olarak görüntüleyen bir denetim.

- <xref:System.Windows.Forms.TextBox>XML dosyası IÇIN XML şemasını görüntüleyen bir denetim.

- İki <xref:System.Windows.Forms.Button> Denetim.

  - Bir düğme XML dosyasını veri kümesine okur ve <xref:System.Windows.Forms.DataGridView> denetimde görüntüler.

  - İkinci bir düğme, şemayı veri kümesinden ayıklar ve bir ile <xref:System.IO.StringWriter> denetim içinde görüntüler <xref:System.Windows.Forms.TextBox> .

#### <a name="to-add-controls-to-the-form"></a>Forma denetim eklemek için

1. `Form1`Tasarım görünümünde açın.

2. **Araç kutusundan**aşağıdaki denetimleri form üzerine sürükleyin:

    - Tek <xref:System.Windows.Forms.DataGridView> Denetim

    - Tek <xref:System.Windows.Forms.TextBox> Denetim

    - İki <xref:System.Windows.Forms.Button> Denetim

3. Aşağıdaki özellikleri ayarlayın:

    |Denetim|Özellik|Ayar|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Çubuklarını**|**Dikey**|
    |`Button1`|**Ad**|`ReadXmlButton`|
    ||**Metin**|`Read XML`|
    |`Button2`|**Ad**|`ShowSchemaButton`|
    ||**Metin**|`Show Schema`|

## <a name="create-the-dataset-thatreceives-the-xml-data"></a>XML verilerini alan veri kümesini oluşturma
 Bu adımda adlı yeni bir veri kümesi oluşturursunuz `authors` . Veri kümeleri hakkında daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

#### <a name="to-create-a-new-dataset-that--receives-the-xml-data"></a>XML verilerini alan yeni bir veri kümesi oluşturmak için

1. **Çözüm Gezgini**, **Form1**için kaynak dosyasını seçin ve sonra **Çözüm Gezgini** araç çubuğunda **Tasarımcı görüntüle** düğmesini seçin.

2. [Araç kutusu, veri sekmesinde](../ide/reference/toolbox-data-tab.md)bir **veri kümesini** **Form1**üzerine sürükleyin.

3. **Veri kümesi Ekle** Iletişim kutusunda **türsüz veri kümesi**' ni seçin ve ardından **Tamam**' ı seçin.

     **DataSet1** , bileşen tepsisine eklenir.

4. **Özellikler** penceresinde, **adını** ve <xref:System.Data.DataSet.DataSetName%2A> özelliklerini ayarlayın `AuthorsDataSet` .

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>XML dosyasını veri kümesine okumak için olay işleyicisini oluşturma
 **XML oku** düğmesi XML dosyasını veri kümesine okur. Daha sonra bu <xref:System.Windows.Forms.DataGridView> Denetim, veri kümesine bağlayan denetimdeki özellikleri ayarlar.

#### <a name="to-add-code-to-the-readxmlbutton_click-event-handler"></a>ReadXmlButton_Click olay işleyicisine kod eklemek için

1. **Çözüm Gezgini**, **Form1**' i seçin ve sonra **Çözüm Gezgini** araç çubuğunda **Tasarımcı görüntüle** düğmesini seçin.

2. **XML oku** düğmesini seçin.

     **Kod Düzenleyicisi** `ReadXmlButton_Click` olay işleyicisinde açılır.

3. Olay işleyicisine aşağıdaki kodu yazın `ReadXmlButton_Click` :

     [!code-csharp[VbRaddataFillingAndExecuting#2](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#2)]
     [!code-vb[VbRaddataFillingAndExecuting#2](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#2)]

4. `ReadXMLButton_Click`Olay işleyicisi kodunda, `filepath =` girişi doğru yola değiştirin.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Metin kutusu içinde şemayı göstermek için olay işleyicisini oluşturma
 **Şemayı göster** düğmesi, <xref:System.IO.StringWriter> şemayla doldurulmuş ve denetimde görüntülenen bir nesne oluşturur <xref:System.Windows.Forms.TextBox> .

#### <a name="to-add-code-to-the-showschemabutton_click-event-handler"></a>ShowSchemaButton_Click olay işleyicisine kod eklemek için

1. **Çözüm Gezgini**, **Form1**' i seçin ve sonra **Tasarımcı görüntüle** düğmesini seçin.

2. **Şemayı göster** düğmesini seçin.

     **Kod Düzenleyicisi** `ShowSchemaButton_Click` olay işleyicisinde açılır.

3. Olay işleyicisine aşağıdaki kodu yazın `ShowSchemaButton_Click` .

     [!code-csharp[VbRaddataFillingAndExecuting#3](../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs#3)]
     [!code-vb[VbRaddataFillingAndExecuting#3](../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb#3)]

## <a name="test-the-form"></a>Formu test etme

Artık, beklenen şekilde davrandığından emin olmak için formu test edebilirsiniz.

1. Uygulamayı çalıştırmak için **F5** ' i seçin.

2. **XML oku** düğmesini seçin.

     DataGridView, XML dosyasının içeriğini görüntüler.

3. **Şemayı göster** düğmesini seçin.

     Metin kutusu XML dosyası için XML şemasını görüntüler.

## <a name="next-steps"></a>Sonraki Adımlar

Bu izlenecek yol, bir XML dosyasını bir veri kümesine okumayla ilgili temel bilgileri ve XML dosyasının içeriğine göre bir şema oluşturmayı öğretir. Daha sonra gerçekleştirebileceğiniz bazı görevler şunlardır:

- Veri kümesindeki verileri düzenleyin ve XML olarak yeniden yazın. Daha fazla bilgi için bkz. <xref:System.Data.DataSet.WriteXml%2A>.

- Veri kümesindeki verileri düzenleyin ve veritabanına yazın.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual [Studio 'da veri erişimi](../data-tools/accessing-data-in-visual-studio.md) için [veri,](https://msdn.microsoft.com/library/15a88fb8-3bee-4962-914d-7a1f8bd40ec4) Visual Studio 'Da veri [XML araçları](../xml-tools/xml-tools-in-visual-studio.md) [almak üzere hazırlama](https://msdn.microsoft.com/library/c17bdb7e-c234-4f2f-9582-5e55c27356ad)

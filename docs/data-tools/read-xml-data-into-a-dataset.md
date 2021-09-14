---
title: Bir veri kümesinin içine XML verileri okuma
description: XML verilerini bir veri kümesine okuma. Bu kılavuzda, XML verilerini bir Windows veri kümesine yükecek bir uygulama oluşturabileceksiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: 9fe6058713abf66ab173f4ddf77e9ff71a03bb74
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631239"
---
# <a name="read-xml-data-into-a-dataset"></a>Bir veri kümesinin içine XML verileri okuma

ADO.NET XML verileriyle çalışmak için basit yöntemler sağlar. Bu kılavuzda, XML verilerini bir Windows veri kümesine yükecek bir uygulama oluşturabileceksiniz. Veri kümesi daha sonra bir denetimde <xref:System.Windows.Forms.DataGridView> görüntülenir. Son olarak, XML dosyasının içeriğini temel alan bir XML şeması bir metin kutusunda görüntülenir.

## <a name="create-a-new-project"></a>Yeni proje oluşturma

C# **veya Windows için yeni** bir FormLar Uygulaması projesi Visual Basic. Projeye **ReadingXML adını girin.**

## <a name="generate-the-xml-file-to-be-read-into-the-dataset"></a>Veri kümesine okunabilecek XML dosyasını oluşturma

Bu kılavuz, XML verilerini bir veri kümesinde okumaya odaklanan bir XML dosyasının içeriği sağlanır.

1. Yeni **Project** **Ekle'yi seçin.**

2. **XML Dosyası'authors.xml,** **dosyayı olarakauthors.xml** ekle'yi **seçin.**

   XML dosyası tasarımcıya yüklenir ve düzenlemeye hazırdır.

3. Aşağıdaki XML verilerini XML bildiriminin altındaki düzenleyiciye yapıştırın:

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

4. Dosya menüsünde **Kaydet'i** **seçin ve authors.xml.**

## <a name="create-the-user-interface"></a>Kullanıcı arabirimini oluşturma

Bu uygulamanın kullanıcı arabirimi aşağıdakilerden oluşur:

- <xref:System.Windows.Forms.DataGridView>XML dosyasının içeriğini veri olarak görüntüleyen denetim.

- XML <xref:System.Windows.Forms.TextBox> dosyası için XML şemasını görüntüleyen bir denetim.

- İki <xref:System.Windows.Forms.Button> denetim.

  - Bir düğme, XML dosyasını veri kümesine okur ve denetimde <xref:System.Windows.Forms.DataGridView> görüntüler.

  - İkinci bir düğme, veri kümesinden şemayı ayıklar ve aracılığıyla <xref:System.IO.StringWriter> bunu denetimde <xref:System.Windows.Forms.TextBox> görüntüler.

### <a name="to-add-controls-to-the-form"></a>Forma denetim eklemek için

1. Tasarım `Form1` görünümünde açın.

2. Araç **Kutusundan** aşağıdaki denetimleri forma sürükleyin:

    - Tek <xref:System.Windows.Forms.DataGridView> denetim

    - Tek <xref:System.Windows.Forms.TextBox> denetim

    - İki <xref:System.Windows.Forms.Button> denetim

3. Aşağıdaki özellikleri ayarlayın:

    |Denetim|Özellik|Ayar|
    |-------------|--------------|-------------|
    |`TextBox1`|**Multiline**|`true`|
    ||**Scrollbars**|**Dikey**|
    |`Button1`|**Ad**|`ReadXmlButton`|
    ||**Metin**|`Read XML`|
    |`Button2`|**Ad**|`ShowSchemaButton`|
    ||**Metin**|`Show Schema`|

## <a name="create-the-dataset-that-receives-the-xml-data"></a>XML verilerini alan veri kümesi oluşturma

Bu adımda adlı yeni bir veri kümesi `authors` oluşturabilirsiniz. Veri kümeleri hakkında daha fazla bilgi için [bkz.](../data-tools/dataset-tools-in-visual-studio.md)Visual Studio.

1. Bu **Çözüm Gezgini** **Form1** için kaynak dosyasını seçin ve ardından araç **çubuğundaki Görünüm Tasarımcısı** düğmesini **Çözüm Gezgini** seçin.

2. Araç [Kutusu,Veri sekmesinden bir](../ide/reference/toolbox-data-tab.md) **DataSet'i** **Form1'e sürükleyin.**

3. Veri Kümesi **Ekle iletişim kutusunda,** Türlanmamış **veri kümesi 'i ve ardından** Tamam'ı **seçin.**

     **DataSet1** bileşen tepsisine eklenir.

4. Özellikler **penceresinde,** için Ad **ve** <xref:System.Data.DataSet.DataSetName%2A> özellikler'i `AuthorsDataSet` ayarlayın.

## <a name="create-the-event-handler-to-read-the-xml-file-into-the-dataset"></a>XML dosyasını veri kümesine okumak için olay işleyicisi oluşturma

**XML'i** Oku düğmesi, XML dosyasını veri kümesine okur. Ardından denetimde, <xref:System.Windows.Forms.DataGridView> bunu veri kümesine bağlayan özellikleri ayarlar.

1. Bu **Çözüm Gezgini** **Form1'i** seçin ve ardından araç **çubuğunda Görünüm Tasarımcısı** **düğmeyi Çözüm Gezgini** seçin.

2. XML Oku **düğmesini** seçin.

     Kod **Düzenleyicisi olay** işleyicisinde `ReadXmlButton_Click` açılır.

3. Olay işleyicisine aşağıdaki `ReadXmlButton_Click` kodu yazın:

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet2":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet2":::

4. Olay `ReadXMLButton_Click` işleyicisi kodunda `filepath =` girdiyi doğru yola göre değiştirebilirsiniz.

## <a name="create-the-event-handler-to-display-the-schema-in-the-textbox"></a>Şemayı metin kutusunda görüntülemek için olay işleyicisi oluşturma

**Şemayı** Göster düğmesi <xref:System.IO.StringWriter> şemayla doldurulmuş bir nesne oluşturur ve denetimde <xref:System.Windows.Forms.TextBox> görüntülenir.

1. Bu **Çözüm Gezgini** **Form1'i** ve ardından Form1 düğmesini **Görünüm Tasarımcısı** seçin.

2. Şemayı **Göster düğmesini** seçin.

     Kod **Düzenleyicisi olay** işleyicisinde `ShowSchemaButton_Click` açılır.

3. Aşağıdaki kodu olay `ShowSchemaButton_Click` işleyicisine yapıştırın.

     :::code language="csharp" source="../snippets/csharp/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/CS/Form1.cs" id="Snippet3":::
     :::code language="vb" source="../snippets/visualbasic/VS_Snippets_VBCSharp/VbRaddataFillingAndExecuting/VB/Form1.vb" id="Snippet3":::

## <a name="test-the-form"></a>Formu test etmek

Artık formu test etmek için beklendiği gibi davranarak emin olun.

1. Uygulamayı **çalıştırmak için F5'i** seçin.

2. XML Oku **düğmesini** seçin.

     DataGridView, XML dosyasının içeriğini görüntüler.

3. Şemayı **Göster düğmesini** seçin.

     Metin kutusunda XML dosyasının XML şeması görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar

Bu kılavuzda, xml dosyasını bir veri kümesine okumanın yanı sıra XML dosyasının içeriğine göre bir şema oluşturmanın temelleri öğretildi. Bundan sonra gerçekleştirebilirsiniz bazı görevler:

- Veri kümesinde verileri düzenleyin ve XML olarak geri yazın. Daha fazla bilgi için bkz. <xref:System.Data.DataSet.WriteXml%2A>.

- Veri kümesinde verileri düzenleyin ve bir veritabanına yazın.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere erişime](../data-tools/accessing-data-in-visual-studio.md)
- [Visual Studio'daki XML araçları](../xml-tools/xml-tools-in-visual-studio.md)

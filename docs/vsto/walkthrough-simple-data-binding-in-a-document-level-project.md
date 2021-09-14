---
title: 'Adım adım kılavuz: Belge düzeyi projesinde basit veri bağlama'
description: Bir belge düzeyi projesinde veri bağlamanın temellerini ve bir SQL Server veritabanındaki tek bir veri alanı için Microsoft Excel.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data binding [Office development in Visual Studio], worksheet cell to Database field
- worksheets [Office development in Visual Studio], binding worksheet cell to Database field
- Database field [Office development in Visual Studio]
- data [Office development in Visual Studio], binding data
- simple data binding [Office development in Visual Studio]
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: c965b63c4f7aec8229fce45be95b5b7c74bd0c96
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725543"
---
# <a name="walkthrough-simple-data-binding-in-a-document-level-project"></a>Adım adım kılavuz: Belge düzeyi projesinde basit veri bağlama
  Bu kılavuzda, belge düzeyindeki bir projede veri bağlamanın temelleri anlattır. SQL Server veritabanındaki tek bir veri alanı, veri kaynağında adlandırılmış bir Microsoft Office Excel. Adım adım kılavuz, tablodaki tüm kayıtlar arasında kaydırmanıza olanak sağlayan denetimlerin nasıl ekli olduğunu da gösterir.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Excel projesi için veri kaynağı oluşturma.

- Çalışma sayfasına denetimler ekleme.

- Veritabanı kayıtları arasında kaydırma.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Northwind veritabanı ile bir sunucuya erişim SQL Server veritabanı.

- Veri veritabanından okuma ve veritabanına SQL Server izinleri.

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 Bu adımda bir çalışma kitabı projesi Excel oluşturabilirsiniz.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. Visual Basic Excel veya C# kullanarak Basit Veri Bağlamam adıyla bir Visual Basic çalışma kitabı projesi oluşturun. Yeni belge **oluştur'ın seçili olduğundan** emin olun. Daha fazla bilgi için, [bkz. How to: Create Office projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

   Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve My **Simple Data Binding** projesini Çözüm Gezgini. 

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma
 Projenize **türü** türüne göre bir veri kümesi eklemek için Veri Kaynakları penceresini kullanın.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. Veri **Kaynakları penceresi görünmüyorsa,** menü çubuğunda Diğer Kaynakları Görüntüle'Windows   >    >  **görüntüleniyor.**

2. Veri **Kaynağı Yapılandırma Sihirbazı'nı başlatmak** için Yeni Veri Kaynağı **Ekle'yi seçin.**

3. **Veritabanı'yı seçin** ve ardından Sonraki'ye **tıklayın.**

4. Northwind örnek veritabanına bir veri SQL Server seçin veya Yeni Bağlantı düğmesini kullanarak yeni **bir bağlantı** ekleyin.

5. Bir bağlantı seçildikten veya oluşturulduktan sonra, Sonraki'ne **tıklayın.**

6. Bağlantı seçiliyse, bağlantıyı kaydetme seçeneğinin temizlemesi ve ardından Sonraki'ye **tıklayın.**

7. Veritabanı **nesneleri** penceresinde Tablolar **düğümünü** genişletin.

8. Müşteriler tablosu yanındaki onay **kutusunu** seçin.

9. **Finish (Son)** düğmesine tıklayın.

   Sihirbaz, Veri **Kaynakları penceresine** Customers **tablosu** ekler. Ayrıca, projenize yazarak yazarak **Çözüm Gezgini.**

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Bu kılavuz için, ilk çalışma sayfasında iki adlandırılmış aralık ve dört düğme gerekir. İlk olarak, veri kaynağına otomatik olarak **bağlı olacak** şekilde Veri Kaynakları penceresinden iki adlandırılmış aralığı ekleyin. Ardından Araç Kutusundan düğmeleri **ekleyin.**

### <a name="to-add-two-named-ranges"></a>İki adlandırılmış aralık eklemek için

1. Sayfa1'in *görüntülendiğinden Binding.xlsx* Veri Verilerim çalışma kitabının Visual Studio **olduğunu** doğrulayın.

2. Veri **Kaynakları penceresini** açın ve Müşteriler **düğümünü** genişletin.

3. **CompanyName sütununu** seçin ve açılan oka tıklayın.

4. Açılan **listeden NamedRange'i** seçin ve **CompanyName** sütununu **A1 hücresine sürükleyin.**

     <xref:Microsoft.Office.Tools.Excel.NamedRange> `companyNameNamedRange` A1 hücresinde adlı bir **denetim oluşturulur.** Aynı zamanda, adlı <xref:System.Windows.Forms.BindingSource> `customersBindingSource` bir , tablo bağdaştırıcısı ve bir örnek <xref:System.Data.DataSet> projeye eklenir. Denetim, örneğine <xref:System.Windows.Forms.BindingSource> bağlı olan denetimine <xref:System.Data.DataSet> bağımlıdır.

5. Veri **Kaynakları penceresinde CustomerID** **sütununu** seçin ve açılan oka tıklayın.

6. Açılan **listede NamedRange'e** tıklayın ve **CustomerID** sütununu **B1 hücresine sürükleyin.**

7. <xref:Microsoft.Office.Tools.Excel.NamedRange>adlı başka bir denetim `customerIDNamedRange` **B1 hücresinde oluşturulur** ve hücresine bağlı <xref:System.Windows.Forms.BindingSource> olur.

### <a name="to-add-four-buttons"></a>Dört düğme eklemek için

1. Araç **Kutusunun Ortak Denetimler** **sekmesinden,** çalışma sayfasının <xref:System.Windows.Forms.Button> **A3 hücresine bir** denetim ekleyin.

    Bu düğme olarak `Button1` adlandırılmıştır.

2. Adların gösterildiği gibi olacak şekilde bu sırayla aşağıdaki hücrelere üç düğme daha ekleyin:

   |Cep|(Ad)|
   |----------|--------------|
   |B3|Düğme2|
   |C3|Düğme3|
   |D3|Düğme4|

   Sonraki adım düğmelere metin eklemek ve C# içinde olay işleyicileri eklemektir.

## <a name="initialize-the-controls"></a>Denetimleri başlatma
 Düğme metnini ayarlayın ve olay sırasında olay işleyicileri <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> ekleyin.

### <a name="to-initialize-the-controls"></a>Denetimleri başlatmak için

1. Bu **Çözüm Gezgini,** **Sayfa1.vb veya Sheet1.cs'ye** sağ **tıklayın** ve ardından kısayol menüsünde **Kodu** Görüntüle'ye tıklayın.

2. Her düğmenin metnini ayarlamak `Sheet1_Startup` için aşağıdaki kodu yöntemine ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet2":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet2":::

3. Yalnızca C# için, düğmeye tıklayın olayları için olay işleyicilerini yöntemine `Sheet1_Startup` ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet3":::

   Şimdi kullanıcının kayıtlara göz <xref:System.Windows.Forms.Control.Click> atarak düğme olaylarını işlemesi için kod ekleyin.

## <a name="add-code-to-enable-scrolling-through-the-records"></a>Kayıtlarda kaydırmayı etkinleştirmek için kod ekleme
 Kayıtlarda taşımak <xref:System.Windows.Forms.Control.Click> için her düğmenin olay işleyicisi için kod ekleyin.

### <a name="to-move-to-the-first-record"></a>İlk kayda taşımak için

1. Düğmenin olayı için bir <xref:System.Windows.Forms.Control.Click> olay `Button1` işleyicisi ekleyin ve ilk kayda taşımak için aşağıdaki kodu ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet4":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet4":::

### <a name="to-move-to-the-previous-record"></a>Önceki kayda taşımak için

1. Düğmenin olayı için bir olay işleyicisi ekleyin ve konumu tek tek geri taşımak <xref:System.Windows.Forms.Control.Click> `Button2` için aşağıdaki kodu ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet5":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet5":::

### <a name="to-move-to-the-next-record"></a>Sonraki kayda taşımak için

1. Düğmenin olayı için bir <xref:System.Windows.Forms.Control.Click> olay işleyicisi ekleyin ve konumu tek tek `Button3` ilerlemek için aşağıdaki kodu ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet6":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet6":::

### <a name="to-move-to-the-last-record"></a>Son kayda taşımak için

1. Düğmenin olayı için bir olay işleyicisi ekleyin ve son <xref:System.Windows.Forms.Control.Click> kayda taşımak için aşağıdaki kodu `Button4` ekleyin:

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet7":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet7":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık çalışma kitabınızı test etmek için veritabanındaki kayıtlara göz atabilirsiniz.

### <a name="to-test-your-workbook"></a>Çalışma kitabınızı test etmek için

1. Projenizi **çalıştırmak için F5** tuşuna basın.

2. İlk kaydın A1 ve **B1 hücrelerinde** **görüntülendiğinden onaylayın.**

3. ( **>** `Button3` ) düğmesine tıklayın ve sonraki kaydın A1 ve **B1 hücresinde** **görüntülendiğinden onaylayın.**

4. Kaydın beklendiği gibi değiştiklerini onaylamak için diğer kaydırma düğmelerine tıklayın.

## <a name="next-steps"></a>Sonraki adımlar
 Bu kılavuz, adlandırılmış bir aralığı veritabanındaki bir alana bağlamanın temellerini gösterir. Bir sonraki görevlerden bazıları:

- Çevrimdışı olarak kullanılana kadar verileri önbelleğe alın. Daha fazla bilgi için [bkz. Nasıl kullanılır: Verileri çevrimdışı veya bir sunucuda kullanmak üzere önbelleğe alın.](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)

- Hücreleri bir alan yerine tablodaki birden çok sütuna bağlayın. Daha fazla bilgi için [bkz. Belge düzeyi projesinde adım adım kılavuz: Karmaşık veri bağlama.](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)

- Kayıtlar <xref:System.Windows.Forms.BindingNavigator> arasında kaydırma yapmak için bir denetim kullanın. Daha fazla bilgi için, [bkz. How to: Navigate data with the Windows Forms BindingNavigator control](/dotnet/framework/winforms/controls/bindingnavigator-control-overview-windows-forms).

## <a name="see-also"></a>Ayrıca bkz.
- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Veri Office verileri](../vsto/data-in-office-solutions.md)
- [Adım adım kılavuz: Belge düzeyi projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md)

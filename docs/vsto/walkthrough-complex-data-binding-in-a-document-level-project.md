---
title: 'Adım adım kılavuz: Belge düzeyi projesinde karmaşık veri bağlama'
description: Çalışma sayfasındaki birden çok hücreyi Northwind Microsoft Excel veritabanındaki alanlara nasıl SQL Server öğrenin.
ms.custom: SEO-VS-2020
titleSuffix: ''
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data [Office development in Visual Studio], binding data
- complex data [Office development in Visual Studio]
- multiple column data binding [Office development in Visual Studio]
- data binding [Office development in Visual Studio], multiple columns
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ac951f07fc31c901f79b0116ff325be9fb64c0d7
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122147576"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>Adım adım kılavuz: Belge düzeyi projesinde karmaşık veri bağlama
  Bu kılavuzda, belge düzeyindeki bir projede karmaşık veri bağlamanın temelleri anlattır. Çalışma sayfasındaki birden çok hücreyi northwind Microsoft Office Excel veritabanındaki alanlara SQL Server bekleyebilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma kitabı projenize veri kaynağı ekleme.

- Çalışma sayfasına veriye bağlı denetimler ekleme.

- Veri değişikliklerini veritabanına geri kaydetme.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Northwind veritabanı ile bir sunucuya erişim SQL Server veritabanı.

- Veri veritabanından okuma ve veritabanına yazma SQL Server izinler.

## <a name="create-a-new-project"></a>Yeni proje oluşturma
 İlk adım bir çalışma kitabı projesi Excel oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni proje oluşturmak için

1. My Complex Data Binding Excel bir çalışma kitabı **projesi oluşturun.** Sihirbazda Yeni belge **oluştur'a tıklayın.**

     Daha fazla bilgi için, [bkz. How to: Create Office Projects in Visual Studio.](../vsto/how-to-create-office-projects-in-visual-studio.md)

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve Karmaşık Veri Bağlamam **projesini** **Çözüm Gezgini.**

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

8. Çalışanlar tablosu yanındaki onay **kutusunu** seçin.

9. **Finish (Son)** düğmesine tıklayın.

   Sihirbaz, Veri **Kaynakları penceresine** Employees **tablosu** ekler. Ayrıca, projenize, içinde görünen türü belirtilen bir veri kümesi **Çözüm Gezgini.**

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Çalışma sayfası açıldığında **Employees** tablosu görüntülenir. Kullanıcılar, verilerde değişiklik yapacak ve ardından bir düğmeye tıklayarak bu değişiklikleri veritabanına geri kaydedecek.

 Çalışma sayfasını tabloya otomatik olarak bağlamak için Veri Kaynakları <xref:Microsoft.Office.Tools.Excel.ListObject> penceresinden çalışma sayfasına bir **denetim ekleyebilirsiniz.** Kullanıcıya değişiklikleri kaydetme seçeneği vermek için Araç <xref:System.Windows.Forms.Button> Kutusundan bir **denetim ekleyin.**

#### <a name="to-add-a-list-object"></a>Liste nesnesi eklemek için

1. Karmaşık Verilerim çalışma Binding.xlsxçalışma **kitabının,** **Sayfa1'in** görüntü Visual Studio açık olduğunu doğrulayın.

2. Veri **Kaynakları penceresini** açın ve Çalışanlar **düğümünü** seçin.

3. Açılan oka tıklayın.

4. Açılan **listeden ListObject** öğesini seçin.

5. Employees tablosu **A6** **hücresine sürükleyin.**

     <xref:Microsoft.Office.Tools.Excel.ListObject> `EmployeesListObject` A6 hücresinde adlı bir **denetim oluşturulur.** Aynı zamanda, adlı <xref:System.Windows.Forms.BindingSource> `EmployeesBindingSource` bir , tablo bağdaştırıcısı ve bir örnek <xref:System.Data.DataSet> projeye eklenir. Denetim, örneğine <xref:System.Windows.Forms.BindingSource> bağlı olan denetimine <xref:System.Data.DataSet> bağımlıdır.

### <a name="to-add-a-button"></a>Düğme eklemek için

1. Araç **Kutusunun Ortak Denetimler** **sekmesinden,** çalışma sayfasının <xref:System.Windows.Forms.Button> **A4 hücresine bir** denetim ekleyin.

   Sonraki adım, çalışma sayfası açıldığında düğmeye metin eklemektir.

## <a name="initialize-the-control"></a>Denetimi başlatma
 Olay işleyicisinde düğmeye <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup> metin ekleyin.

### <a name="to-initialize-the-control"></a>Denetimi başlatmak için

1. Bu **Çözüm Gezgini,** **Sayfa1.vb veya Sheet1.cs'ye** sağ **tıklayın** ve ardından kısayol menüsünde **Kodu** Görüntüle'ye tıklayın.

2. b metnini ayarlamak `Sheet1_Startup` için aşağıdaki kodu yöntemine `utton` ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet8":::
    :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet8":::

3. Yalnızca C# için, yöntemine olayı için <xref:System.Windows.Forms.Control.Click> bir olay `Sheet1_Startup` işleyicisi ekleyin.

    :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet9":::

   Şimdi düğmenin olaylarını <xref:System.Windows.Forms.Control.Click> işlemek için kod ekleyin.

## <a name="save-changes-to-the-database"></a>Değişiklikleri veritabanına kaydetme
 Verilerde yapılan tüm değişiklikler, açıkça veritabanına geri kaydedilene kadar yalnızca yerel veri kümesinde mevcuttur.

### <a name="to-save-changes-to-the-database"></a>Veritabanındaki değişiklikleri kaydetmek için

1. olayı için bir olay işleyicisi ekleyin ve veri kümesinde yapılan tüm değişiklikleri veritabanına geri işlemek <xref:System.Windows.Forms.Control.Click> `button` için aşağıdaki kodu ekleyin.

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs" id="Snippet10":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb" id="Snippet10":::

## <a name="test-the-application"></a>Uygulamayı test edin
 Artık çalışma kitabınızı test etmek için verilerin beklendiği gibi görüntülendiğinden ve liste nesnesinde verileri işleyebilirsiniz.

### <a name="to-test-the-data-binding"></a>Veri bağlamayı test etmek için

- **F5 tuşuna basın.**

     Çalışma kitabı açıldığında liste nesnesinin Employees tablosundan gelen verilerle **doldurulması gerekir.**

### <a name="to-modify-data"></a>Verileri değiştirmek için

1. Davolio **adını içermesi** gereken B7 **hücresine tıklayın.**

2. Anderson adını **yazın** ve Enter tuşuna **basın.**

### <a name="to-modify-a-column-header"></a>Sütun üst bilgilerini değiştirmek için

1. LastName sütun başlığını içeren **hücreye tıklayın.**

2. İki **sözcük arasına** boşluk da dahil olmak üzere Soyadı yazın ve Enter tuşuna **basın.**

### <a name="to-save-data"></a>Verileri kaydetmek için

1. Çalışma **sayfasında Kaydet'e** tıklayın.

2. Çıkış Excel. Yaptığınız **değişiklikleri** kaydetmek için istendiğinde Hayır'a tıklayın.

3. Projeyi **yeniden çalıştırmak için F5** tuşuna basın.

     List nesnesi Employees tablosundan **verilerle** doldurulur.

4. **B7** hücresinde adın hala **Anderson** olduğunu ve bu değişikliğin veritabanına geri kaydeden veri değişikliği olduğunu fark etmek gerekir. Sütun üst bilgisi veritabanına bağlı değildir ve çalışma sayfasında yaptığınız değişiklikleri kaydetmemiş olduğundan **LastName** sütun üst bilgisi özgün biçimine geri dönmektedir.

### <a name="to-add-new-rows"></a>Yeni satırlar eklemek için

1. Liste nesnesinin içinde bir hücre seçin.

    Listenin en altında, yeni satırın ilk hücresinde yıldız işareti ( ) olan **\*** yeni bir satır görüntülenir.

2. Boş satıra aşağıdaki bilgileri ekleyin.

   |Çalışan Kimliği|LastName|FirstName|Başlık|
   |----------------|--------------|---------------|-----------|
   |10|ıto|Shu|Satış Yöneticisi|

### <a name="to-delete-rows"></a>Satırları silmek için

- Çalışma sayfasının en sol tarafındaki 16 sayısına (satır 16) sağ tıklayın ve ardından Sil'e **tıklayın.**

### <a name="to-sort-the-rows-in-the-list"></a>Liste'de satırları sıralamak için

1. Listenin içinde bir hücre seçin.

     Her sütun başlığında ok düğmeleri görünür.

2. Soyadı sütun üst bilgisinde **ok düğmesine** tıklayın.

3. **Artan sıralama**' ya tıklayın.

     Satırlar, son adlara göre alfabetik olarak sıralanır.

### <a name="to-filter-information"></a>Bilgileri filtrelemek için

1. Listenin içinde bir hücre seçin.

2. **Başlık** sütunu üstbilgisindeki ok düğmesine tıklayın.

3. **Satış temsilcisi**' ne tıklayın.

     Liste yalnızca **başlık** sütununda **satış temsilcisi** olan satırları gösterir.

4. **Başlık** sütun üstbilgisindeki ok düğmesine tekrar tıklayın.

5. **(Tümü)** seçeneğine tıklayın.

     Filtreleme kaldırılır ve tüm satırlar görüntülenir.

## <a name="next-steps"></a>Sonraki adımlar
 Bu izlenecek yol, bir veritabanındaki tabloyu bir liste nesnesine bağlamanın temellerini gösterir. Daha sonra gelebilecek bazı görevler şunlardır:

- Çevrimdışı kullanılabilmesi için verileri önbelleğe alma. Daha fazla bilgi için bkz. [nasıl yapılır: çevrimdışı kullanım için verileri önbelleğe alma veya bir sunucu üzerinde](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).

- Çözümü dağıtın. daha fazla bilgi için bkz. [Office çözüm dağıtma](../vsto/deploying-an-office-solution.md).

- Bir alanla tablo arasında ana/ayrıntı ilişkisi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: önbelleğe alınmış bir veri kümesini kullanarak ana ayrıntı Ilişkisi oluşturma](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office çözümlerinde veri](../vsto/data-in-office-solutions.md)
- [İzlenecek yol: belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)

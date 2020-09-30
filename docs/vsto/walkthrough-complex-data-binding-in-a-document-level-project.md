---
title: 'İzlenecek yol: belge düzeyi projede karmaşık veri bağlama'
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7aba307bcd76cc055e42c11418d42f3dd0cfba1f
ms.sourcegitcommit: 9d2829dc30b6917e89762d602022915f1ca49089
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/30/2020
ms.locfileid: "91584327"
---
# <a name="walkthrough-complex-data-binding-in-a-document-level-project"></a>İzlenecek yol: belge düzeyi projede karmaşık veri bağlama
  Bu izlenecek yol, belge düzeyindeki bir projede karmaşık veri bağlamanın temellerini gösterir. Microsoft Office Excel çalışma sayfasındaki birden çok hücreyi Northwind SQL Server veritabanındaki alanlara bağlayabilirsiniz.

 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

 Bu izlenecek yol aşağıdaki görevleri gösterir:

- Çalışma kitabı projenize veri kaynağı ekleme.

- Çalışma sayfasına veriye dayalı denetimler ekleme.

- Veri değişiklikleri veritabanına geri kaydediliyor.

  [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]

## <a name="prerequisites"></a>Önkoşullar
 Bu izlenecek yolu tamamlamak için aşağıdaki bileşenlere ihtiyacınız vardır:

- [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]

- [!INCLUDE[Excel_15_short](../vsto/includes/excel-15-short-md.md)] veya [!INCLUDE[Excel_14_short](../vsto/includes/excel-14-short-md.md)].

- Northwind SQL Server örnek veritabanıyla bir sunucuya erişim.

- SQL Server veritabanına okuma ve yazma izinleri.

## <a name="create-a-new-project"></a>Yeni bir proje oluşturma
 İlk adım bir Excel çalışma kitabı projesi oluşturmaktır.

### <a name="to-create-a-new-project"></a>Yeni bir proje oluşturmak için

1. **Karmaşık veri bağlamamı**adlı bir Excel çalışma kitabı projesi oluşturun. Sihirbazda **Yeni belge oluştur**' u seçin.

     Daha fazla bilgi için bkz. [nasıl yapılır: Visual Studio 'Da Office projeleri oluşturma](../vsto/how-to-create-office-projects-in-visual-studio.md).

     Visual Studio tasarımcıda yeni Excel çalışma kitabını açar ve **karmaşık veri bağlama** projesini **Çözüm Gezgini**ekler.

## <a name="create-the-data-source"></a>Veri kaynağını oluşturma
 Projenize türü belirtilmiş bir veri kümesi eklemek için **veri kaynakları** penceresini kullanın.

### <a name="to-create-the-data-source"></a>Veri kaynağı oluşturmak için

1. **Veri kaynakları** penceresi görünür değilse, menü çubuğunda, **View**  >  **diğer Windows**  >  **veri kaynaklarını**görüntüle ' yi seçerek bunu görüntüleyin.

2. **Veri kaynağı Yapılandırma Sihirbazı 'nı**başlatmak Için **Yeni veri kaynağı Ekle** ' yi seçin.

3. **Veritabanı** ' nı seçin ve ardından **İleri**' ye tıklayın.

4. Northwind örnek SQL Server veritabanına yönelik bir veri bağlantısı seçin veya **Yeni bağlantı** düğmesini kullanarak yeni bir bağlantı ekleyin.

5. Bir bağlantı seçildikten veya oluşturulduktan sonra **İleri**' ye tıklayın.

6. Seçildiğinde bağlantıyı kaydetme seçeneğini temizleyin ve ardından **İleri**' ye tıklayın.

7. **Veritabanı nesneleri** penceresinde **Tablolar** düğümünü genişletin.

8. **Çalışanlar** tablosunun yanındaki onay kutusunu işaretleyin.

9. **Son**'a tıklayın.

   Sihirbaz, **çalışanlar** tablosunu **veri kaynakları** penceresine ekler. Ayrıca, projenize **Çözüm Gezgini**görünür bir veri kümesi de ekler.

## <a name="add-controls-to-the-worksheet"></a>Çalışma sayfasına denetimler ekleme
 Çalışma kitabı açıldığında, çalışma sayfasında **çalışanlar** tablosu görüntülenir. Kullanıcılar verilerde değişiklik yapabilirler ve ardından bir düğmeye tıklayarak bu değişiklikleri veritabanına geri kaydedebilecektir.

 Çalışma sayfasını tabloya otomatik olarak bağlamak için <xref:Microsoft.Office.Tools.Excel.ListObject> **veri kaynakları** penceresinden çalışma sayfasına bir denetim ekleyebilirsiniz. Kullanıcıya değişiklikleri kaydetme seçeneğini vermek için <xref:System.Windows.Forms.Button> **araç kutusundan**bir denetim ekleyin.

#### <a name="to-add-a-list-object"></a>Bir liste nesnesi eklemek için

1. **Karmaşık veri Binding.xlsx** çalışma kitabının, **Sheet1** görüntülenirken Visual Studio tasarımcısında açık olduğunu doğrulayın.

2. **Veri kaynakları** penceresini açın ve **çalışanlar** düğümünü seçin.

3. Görüntülenen aşağı açılan oka tıklayın.

4. Açılan listede **ListObject** ' i seçin.

5. **Çalışanlar** tablosunu **a6**hücresine sürükleyin.

     <xref:Microsoft.Office.Tools.Excel.ListObject>A6 hücresinde adlı bir denetim `EmployeesListObject` oluşturulur. **A6** Aynı zamanda, <xref:System.Windows.Forms.BindingSource> adlandırılmış `EmployeesBindingSource` , bir tablo bağdaştırıcısı ve <xref:System.Data.DataSet> projeye bir örnek eklenir. Denetim öğesine bağlanır <xref:System.Windows.Forms.BindingSource> , bu da <xref:System.Data.DataSet> örneğe bağlanır.

### <a name="to-add-a-button"></a>Düğme eklemek için

1. **Araç kutusunun** **ortak denetimler** sekmesinden, <xref:System.Windows.Forms.Button> çalışma sayfasının **a4** hücresine bir denetim ekleyin.

   Bir sonraki adım, çalışma sayfası açıldığında düğmeye metin eklemektir.

## <a name="initialize-the-control"></a>Denetimi başlatma
 <xref:Microsoft.Office.Tools.Excel.Worksheet.Startup>Olay işleyicisindeki düğmeye metin ekleyin.

### <a name="to-initialize-the-control"></a>Denetimi başlatmak için

1. **Çözüm Gezgini**, **Sheet1. vb** veya **Sheet1.cs**öğesine sağ tıklayın ve ardından kısayol menüsünde **kodu görüntüle** ' ye tıklayın.

2. `Sheet1_Startup`B için metin ayarlamak üzere yöntemine aşağıdaki kodu ekleyin `utton` .

    [!code-csharp[Trin_VstcoreDataExcel#8](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#8)]
    [!code-vb[Trin_VstcoreDataExcel#8](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#8)]

3. Yalnızca C# için, yöntemine olay için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `Sheet1_Startup` .

    [!code-csharp[Trin_VstcoreDataExcel#9](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#9)]

   Şimdi düğmenin olayını işlemek için kod ekleyin <xref:System.Windows.Forms.Control.Click> .

## <a name="save-changes-to-the-database"></a>Değişiklikleri veritabanına kaydet
 Verilerde yapılan tüm değişiklikler, açıkça veritabanına geri kaydedilinceye kadar yalnızca yerel veri kümesinde bulunur.

### <a name="to-save-changes-to-the-database"></a>Değişiklikleri veritabanına kaydetmek için

1. Olayı için bir olay işleyicisi ekleyin <xref:System.Windows.Forms.Control.Click> `button` ve veri kümesinde yapılan tüm değişiklikleri veritabanına geri kaydetmek için aşağıdaki kodu ekleyin.

     [!code-csharp[Trin_VstcoreDataExcel#10](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet3.cs#10)]
     [!code-vb[Trin_VstcoreDataExcel#10](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet3.vb#10)]

## <a name="test-the-application"></a>Uygulamayı test etme
 Artık, verilerin beklendiği gibi göründüğünü ve liste nesnesindeki verileri işleyebildiğinizi doğrulamak için çalışma kitabınızı test edebilirsiniz.

### <a name="to-test-the-data-binding"></a>Veri bağlamayı test etmek için

- **F5**tuşuna basın.

     Çalışma kitabı açıldığında, liste nesnesinin **çalışanlar** tablosundan alınan verilerle doldurulduğunu doğrulayın.

### <a name="to-modify-data"></a>Verileri değiştirmek için

1. **Etikan**adını Içermesi gereken **B7**hücresini tıklatın.

2. **Anderson**adını yazın ve **ENTER**tuşuna basın.

### <a name="to-modify-a-column-header"></a>Bir sütun üst bilgisini değiştirmek için

1. **Soyadı**sütun başlığını içeren hücreye tıklayın.

2. İki sözcükten oluşan bir boşluk da dahil olmak üzere **Soyadı**yazın ve ardından **ENTER**tuşuna basın.

### <a name="to-save-data"></a>Verileri kaydetmek için

1. Çalışma sayfasında **Kaydet** ' e tıklayın.

2. Excel 'den çıkın. Yaptığınız değişiklikleri kaydetmek isteyip istemediğiniz sorulduğunda **Hayır** ' a tıklayın.

3. Projeyi yeniden çalıştırmak için **F5** 'e basın.

     Liste nesnesi, **çalışanlar** tablosundan alınan verilerle doldurulur.

4. **B7** hücresindeki adın hala **Anderson**olduğunu ve bu durumda, yaptığınız ve veritabanına geri kaydettiğiniz veri değişikliği olduğunu unutmayın. Sütun üst bilgisi veritabanına bağlanmadığından ve çalışma sayfasında yaptığınız değişiklikleri kaydetmediyseniz, **LastName** sütunu, boşluk olmadan özgün biçimine geri değiştirilmiştir.

### <a name="to-add-new-rows"></a>Yeni satırlar eklemek için

1. Liste nesnesi içinde bir hücre seçin.

    Yeni satırın ilk hücresinde bir yıldız işareti () ile listenin en altında yeni bir satır görüntülenir **\*** .

2. Aşağıdaki bilgileri boş satıra ekleyin.

   |Çalışan Kimliği|LastName|FirstName|Başlık|
   |----------------|--------------|---------------|-----------|
   |10|Aslan|Halil|Satış Yöneticisi|

### <a name="to-delete-rows"></a>Satırları silmek için

- Çalışma sayfasının sol tarafında bulunan 16 ' ya (satır 16) sağ tıklayın ve ardından **Sil**' e tıklayın.

### <a name="to-sort-the-rows-in-the-list"></a>Listedeki satırları sıralamak için

1. Listenin içinde bir hücre seçin.

     Her sütun üstbilgisinde ok düğmeleri görünür.

2. **Son ad** sütun üstbilgisindeki ok düğmesine tıklayın.

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

- Çözümü dağıtın. Daha fazla bilgi için bkz. [Office çözümünü dağıtma](../vsto/deploying-an-office-solution.md).

- Bir alanla tablo arasında ana/ayrıntı ilişkisi oluşturun. Daha fazla bilgi için bkz. [Izlenecek yol: önbelleğe alınmış bir veri kümesini kullanarak ana ayrıntı Ilişkisi oluşturma](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)
- [İzlenecek yol: belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md)

---
title: 'Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], data source updates
- data [Office development in Visual Studio], updating a data source from a document
- host controls [Office development in Visual Studio], data source updates
- Office documents [Office development in Visual Studio, data sources
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 8384b35583517a832763f5229d2b526ca10190ad
ms.sourcegitcommit: b885f26e015d03eafe7c885040644a52bb071fae
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/30/2020
ms.locfileid: "85541251"
---
# <a name="how-to-update-a-data-source-with-data-from-a-host-control"></a>Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme
  Bir konak denetimini bir veri kaynağına bağlayabilir ve veri kaynağını denetimdeki verilerde yapılan değişikliklerle güncelleştirebilirsiniz. Bu işlemde iki ana adım vardır:

1. Bellekteki veri kaynağını denetimdeki değiştirilen verilerle güncelleştirin. Genellikle, bellek içi veri kaynağı bir <xref:System.Data.DataSet> , bir <xref:System.Data.DataTable> veya başka bir veri nesnesi olur.

2. Veritabanını, bellek içi veri kaynağındaki değiştirilen verilerle güncelleştirin. Bu, yalnızca veri kaynağı bir SQL Server veya Microsoft Office Access veritabanı gibi bir arka uç veritabanına bağlıysa geçerlidir.

   Konak denetimleri ve veri bağlama hakkında daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md) ve [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md).

   [!INCLUDE[appliesto_controls](../vsto/includes/appliesto-controls-md.md)]

## <a name="update-the-in-memory-data-source"></a>Bellek içi veri kaynağını güncelleştirme
 Varsayılan olarak, basit veri bağlamayı etkinleştiren ana bilgisayar denetimleri (bir Word belgesindeki içerik denetimleri veya bir Excel çalışma sayfasındaki adlandırılmış aralık denetimi), veri değişikliklerini bellek içi veri kaynağına kaydetmez. Diğer bir deyişle, bir son kullanıcı bir konak denetimindeki değeri değiştirdiğinde ve sonra denetimden uzaklaştığında, denetimdeki yeni değer otomatik olarak veri kaynağına kaydedilmez.

 Verileri veri kaynağına kaydetmek için, çalışma zamanında belirli bir olaya yanıt olarak veri kaynağını güncelleştiren bir kod yazabilir veya denetimdeki değer değiştiğinde denetimi veri kaynağını otomatik olarak güncelleştirecek şekilde yapılandırabilirsiniz.

 <xref:Microsoft.Office.Tools.Excel.ListObject>Bellek içi veri kaynağına değişiklikleri kaydetmeniz gerekmez. Veriye bir denetim bağladığınızda <xref:Microsoft.Office.Tools.Excel.ListObject> <xref:Microsoft.Office.Tools.Excel.ListObject> Denetim, ek kod gerekmeden bellekteki veri kaynağına yapılan değişiklikleri otomatik olarak kaydeder.

### <a name="to-update-the-in-memory-data-source-at-run-time"></a>Çalışma zamanında bellek içi veri kaynağını güncelleştirmek için

- <xref:System.Windows.Forms.Binding.WriteValue%2A> <xref:System.Windows.Forms.Binding> Denetimi veri kaynağına bağlayan nesnenin yöntemini çağırın.

     Aşağıdaki örnek, bir <xref:Microsoft.Office.Tools.Excel.NamedRange> Excel çalışma sayfasındaki denetimde yapılan değişiklikleri veri kaynağına kaydeder. Bu örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> bir veri kaynağındaki bir alana bağlanan özelliği ile adlı bir denetiminizin olduğunu varsayar.

     [!code-csharp[Trin_VstcoreDataExcel#1](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#1)]
     [!code-vb[Trin_VstcoreDataExcel#1](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#1)]

### <a name="automatically-update-the-in-memory-data-source"></a>Bellek içi veri kaynağını otomatik olarak güncelleştir
 Ayrıca, bellek içi veri kaynağını otomatik olarak güncelleştiren bir denetimi de yapılandırabilirsiniz. Belge düzeyi projesinde, kodu veya Tasarımcıyı kullanarak bunu yapabilirsiniz. VSTO eklenti projesinde kodu kullanmanız gerekir.

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-code"></a>Kodu kullanarak bellek içi veri kaynağını otomatik olarak güncellemek üzere bir denetim ayarlamak için

1. Denetimi veri kaynağına bağlayan nesnenin System. Windows. Forms. DataSourceUpdateMode. OnPropertyChanged modunu kullanın <xref:System.Windows.Forms.Binding> . Veri kaynağını güncelleştirmek için iki seçenek vardır:

   - Denetim doğrulandığında veri kaynağını güncelleştirmek için, bu özelliği System. Windows. Forms. DataSourceUpdateMode. OnValidation olarak ayarlayın.

   - Denetimin veri bağlantılı özelliğinin değeri değiştiğinde veri kaynağını güncelleştirmek için, bu özelliği System. Windows. Forms. DataSourceUpdateMode. OnPropertyChanged olarak ayarlayın.

     > [!NOTE]
     > Word, belge değişikliği veya Denetim değişikliği bildirimleri sunmadığından, System. Windows. Forms. DataSourceUpdateMode. OnPropertyChanged seçeneği Word konak denetimlerine uygulanmaz. Ancak, bu seçenek Word belgelerindeki Windows Forms denetimleri için kullanılabilir.

     Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimdeki değer değiştiğinde veri kaynağını otomatik olarak güncelleştirmek için bir denetim yapılandırır. Bu örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange> `namedRange1` <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> bir veri kaynağındaki bir alana bağlanan özelliği ile adlı bir denetiminizin olduğunu varsayar.

     [!code-csharp[Trin_VstcoreDataExcel#19](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#19)]
     [!code-vb[Trin_VstcoreDataExcel#19](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#19)]

#### <a name="to-set-a-control-to-automatically-update-the-in-memory-data-source-by-using-the-designer"></a>Tasarımcı kullanarak bellek içi veri kaynağını otomatik olarak güncellemek üzere bir denetim ayarlamak için

1. Visual Studio 'da tasarımcıda Word belgesi veya Excel çalışma kitabı ' nı açın.

2. Veri kaynağını otomatik olarak güncellemek istediğiniz denetime tıklayın.

3. **Özellikler** penceresinde **(DataBindings)** özelliğini genişletin.

4. **(Gelişmiş)** özelliğinin yanında üç nokta düğmesine (![VisualStudioEllipsesButton ekran görüntüsü](../vsto/media/vbellipsesbutton.png "VisualStudioEllipsesButton ekran görüntüsü")) tıklayın.

5. **Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunda, **veri kaynağı güncelleştirme modu** aşağı açılan listesine tıklayın ve aşağıdaki değerlerden birini seçin:

    - Denetim doğrulandığında veri kaynağını güncelleştirmek için **OnValidation**' ı seçin.

    - Denetimin veri bağlantılı özelliğinin değeri değiştiğinde veri kaynağını güncelleştirmek için **OnPropertyChanged**' ı seçin.

        > [!NOTE]
        > Word, belge değişikliği veya Denetim değişikliği bildirimleri sunmadığından, **OnPropertyChanged** seçeneği Word ana bilgisayar denetimlerine uygulanmaz. Ancak, bu seçenek Word belgelerindeki Windows Forms denetimleri için kullanılabilir.

6. **Biçimlendirme ve Gelişmiş bağlama** iletişim kutusunu kapatın.

## <a name="update-the-database"></a>Veritabanını güncelleştirme
 Bellek içi veri kaynağı bir veritabanıyla ilişkiliyse veritabanını veri kaynağındaki değişikliklerle güncelleştirmeniz gerekir. Bir veritabanını güncelleştirme hakkında daha fazla bilgi için bkz. [bir TableAdapter kullanarak](../data-tools/update-data-by-using-a-tableadapter.md) [verileri veritabanına geri kaydetme](../data-tools/save-data-back-to-the-database.md) ve verileri güncelleştirme.

### <a name="to-update-the-database"></a>Veritabanını güncellemek için

1. <xref:System.Windows.Forms.BindingSource.EndEdit%2A> <xref:System.Windows.Forms.BindingSource> Denetim için yöntemini çağırın.

     <xref:System.Windows.Forms.BindingSource>Tasarım zamanında bir belgeye veya çalışma kitabına veri bağlantılı bir denetim eklediğinizde otomatik olarak oluşturulur. , <xref:System.Windows.Forms.BindingSource> Denetimi projenizdeki türü belirtilmiş veri kümesine bağlar. Daha fazla bilgi için bkz. [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview).

     Aşağıdaki kod örneği, projenizin adlandırılmış bir adı içerdiğini varsayar <xref:System.Windows.Forms.BindingSource> `customersBindingSource` .

     [!code-csharp[Trin_VstcoreDataExcel#20](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#20)]
     [!code-vb[Trin_VstcoreDataExcel#20](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#20)]

2. `Update`Projenizde oluşturulan TableAdapter metodunu çağırın.

     Tasarım zamanında bir belgeye veya çalışma kitabına veri bağlantılı bir denetim eklediğinizde TableAdapter otomatik olarak oluşturulur. TableAdapter, projenizdeki türü belirtilmiş veri kümesini veritabanına bağlar. Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

     Aşağıdaki kod örneği, Northwind veritabanındaki Customers tablosuna bir bağlantı olduğunu ve projenizin adlı bir TableAdapter `customersTableAdapter` ve adlı türü belirtilmiş bir veri kümesini içerdiğini varsayar `northwindDataSet` .

     [!code-csharp[Trin_VstcoreDataExcel#21](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#21)]
     [!code-vb[Trin_VstcoreDataExcel#21](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#21)]

## <a name="see-also"></a>Ayrıca bkz.
- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)
- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)

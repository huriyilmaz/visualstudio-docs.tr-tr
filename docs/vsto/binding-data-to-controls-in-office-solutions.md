---
title: Office çözümlerinde verileri denetimlere bağlama
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Office documents [Office development in Visual Studio], connecting to data
- data, data binding
- data binding
- data binding, Office solutions
- data binding, controls
- Office applications [Office development in Visual Studio], data binding
- controls, data binding
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 93e2d5abb9c8fda9d4a1300a9bb0958ac9266499
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72986166"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Office çözümlerinde verileri denetimlere bağlama
  Denetimlerin verileri otomatik olarak görüntülemesi için bir Microsoft Office Word belgesi veya Microsoft Office Excel çalışma sayfası üzerinde Windows Forms denetimleri ve *konak denetimleri* bağlayabilirsiniz. Her iki uygulama düzeyi ve belge düzeyi projesinde, denetimlere veri bağlayabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Konak denetimleri Word ve Excel nesne modelleriyle, Word 'deki içerik denetimleri ve Excel 'de adlandırılmış aralıklar gibi nesneleri genişletir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

 Hem Windows Forms hem de konak denetimleri, hem *basit veri bağlamayı* hem de veri kümeleri ve veri tabloları gibi veri kaynaklarına *karmaşık veri bağlamayı* destekleyen Windows Forms veri bağlama modelini kullanır. Windows Forms veri bağlama modeli hakkında tüm bilgiler için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Basit veri bağlama
 Basit veri bağlama, bir denetim özelliği bir veri tablosundaki değer gibi tek bir veri öğesine bağlandığında oluşur. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi bir veri kümesindeki bir alana bağlanabilen bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğine sahiptir. Veri kümesindeki alanı değiştiğinde, adlandırılmış aralıktaki değeri de değişir. <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimi hariç tüm konak denetimleri, basit veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Word.XMLNodes> denetimi bir koleksiyondur ve bu nedenle veri bağlamayı desteklemez.

 Bir konak denetimine basit veri bağlama gerçekleştirmek için, denetimin `DataBindings` özelliğine bir <xref:System.Windows.Forms.Binding> ekleyin. <xref:System.Windows.Forms.Binding> nesnesi, denetimin özellik değeri ve bir veri öğesinin değeri arasındaki basit bağlamayı temsil eder.

 Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğinin belge düzeyindeki bir projedeki bir veri öğesine nasıl bağlanacağını gösterir.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 Basit veri bağlamayı gösteren izlenecek yollar için bkz. Izlenecek yol: belge düzeyindeki bir proje için [belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) ve bir VSTO eklentisi PROJESI Için [VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) .

## <a name="complex-data-binding"></a>Karmaşık veri bağlama
 Bir denetim özelliği bir veri tablosunda birden çok sütun gibi birden fazla veri öğesine bağlandığında, karmaşık veri bağlama bulunur. Excel için <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi, karmaşık veri bağlamayı destekleyen tek konak denetimidir. Ayrıca, <xref:System.Windows.Forms.DataGridView> denetimi gibi karmaşık veri bağlamayı destekleyen çok sayıda Windows Forms denetimi vardır.

 Karmaşık veri bağlamayı gerçekleştirmek için denetimin `DataSource` özelliğini karmaşık veri bağlama tarafından desteklenen bir veri kaynağı nesnesi olarak ayarlayın. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject> denetiminin <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> özelliği bir veri tablosunda birden çok sütuna bağlanabilir. Veri tablosundaki tüm veriler <xref:Microsoft.Office.Tools.Excel.ListObject> denetiminde görünür ve veri tablosundaki veriler değiştiğinde <xref:Microsoft.Office.Tools.Excel.ListObject> de değişir. Karmaşık veri bağlama için kullanabileceğiniz veri kaynaklarının bir listesi için, bkz. [Windows Forms tarafından desteklenen veri kaynakları](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 Aşağıdaki kod örneği iki <xref:System.Data.DataTable> nesnesi olan bir <xref:System.Data.DataSet> oluşturur ve tablolardan birini verilerle doldurur. Kod daha sonra <xref:Microsoft.Office.Tools.Excel.ListObject> verileri içeren tabloya bağlar. Bu örnek, Excel belge düzeyi projesi içindir.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 Karmaşık veri bağlamayı gösteren izlenecek yollar için bkz. Izlenecek yol: belge düzeyindeki bir proje için [belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) ve bir VSTO eklentisi PROJESI Için [VSTO eklenti projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) .

## <a name="display-data-in-documents-and-workbooks"></a>Belgelerde ve çalışma kitaplarında verileri görüntüleme
 Belge düzeyi projelerde, veri **kaynakları** penceresini kullanarak belgelerinize veya çalışma kitaplarınıza veri bağlantılı denetimleri, Windows Forms için kullandığınız şekilde kolayca ekleyebilirsiniz. **Veri kaynakları** penceresini kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ve [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Denetimleri veri kaynakları penceresinden sürükleyin
 **Veri kaynakları** penceresinden bir nesne üzerine sürüklediğinizde belge üzerinde bir denetim oluşturulur. Oluşturulan denetimin türü, tek bir veri sütununu veya birden çok veri sütununu bağladığınıza bağlıdır.

 Excel 'de, her bir alan için çalışma sayfasında bir <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimi oluşturulur ve birden çok satır ve sütun içeren her bir veri aralığı için bir <xref:Microsoft.Office.Tools.Excel.ListObject> denetimi oluşturulur. Bu varsayılanı, **veri kaynakları** penceresinde tablo veya alanı seçerek ve ardından açılan listeden farklı bir denetim seçerek değiştirebilirsiniz.

 Belgelere bir <xref:Microsoft.Office.Tools.Word.ContentControl> denetimi eklenir. İçerik denetiminin türü, seçtiğiniz alanın veri türüne bağlıdır.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Tasarım zamanında belge düzeyindeki projelere veri bağlama
 Aşağıdaki konularda, tasarım zamanında veri bağlama örnekleri gösterilmektedir:

- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Nasıl yapılır: çalışma sayfasındaki veritabanı kayıtlarını kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>VSTO eklenti projelerinde veri bağlama
 VSTO eklenti projelerinde, yalnızca çalışma zamanında denetim ekleyebilirsiniz. Aşağıdaki konularda çalışma zamanında veri bağlama örnekleri gösterilmektedir:

- [İzlenecek yol: VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [İzlenecek yol: VSTO eklenti projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Konak denetimlerine bağlanan verileri güncelleştirme
 Bir veri kaynağı ve konak denetimi arasındaki veri bağlama iki yönlü bir veri güncelleştirmesi içerir. Basit veri bağlamasında, veri kaynağındaki değişiklikler otomatik olarak konak denetimine yansıtılır, ancak konak denetimindeki değişiklikler veri kaynağını güncelleştirmek için açık bir çağrı gerektirir. Bu nedenle, bir veri bağlantılı alanda yapılan değişikliklere, başka bir veri bağlantılı alandaki değişikliklere eşlik edilmedikleri takdirde, bir veri- Örneğin, biri yaş ve diğeri de deneyim için olmak üzere iki alanı olabilir. Deneyim Age ' i aşamaz. Kullanıcılar, değişiklikleri aynı anda yapamadığı takdirde, 50 ile 25 arasında bir süre güncellenemez ve 30 ' dan 10 ' a kadar deneyim yaşar. Bu sorunu çözmek için, güncelleştirmeler kod tarafından açıkça gönderilene kadar basit veri bağlama içeren alanlar güncellenmez.

 Bir veri kaynağını basit veri bağlamayı etkinleştiren konak denetimlerinden güncelleştirmek için, güncelleştirmeleri bellek içi veri kaynağına (bir <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>) ve arka uç veritabanına (çözümünüz bir tane kullanıyorsa) göndermeniz gerekir.

 <xref:Microsoft.Office.Tools.Excel.ListObject> denetimini kullanarak, karmaşık veri bağlama gerçekleştirdiğinizde bellek içi veri kaynağını açıkça güncelleştirmeniz gerekmez. Bu durumda, değişiklikler ek kod olmadan bellek içi veri kaynağına otomatik olarak gönderilir.

 Daha fazla bilgi için bkz. [nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Nasıl yapılır: bir Windows formunda basit bağlantılı denetim oluşturma](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Önbellek verileri](../vsto/caching-data.md)
- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)

---
title: Office çözümlerinde verileri denetimlere bağlama
description: Bir Microsoft Office Word belgesi veya Excel çalışma sayfasında bir veri kaynağına Windows Forms denetimleri ve konak denetimlerini nasıl bağlayabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 459c50b5f8135756f85de852a62de44b3878148d
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99882485"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Office çözümlerinde verileri denetimlere bağlama
  Denetimlerin verileri otomatik olarak görüntülemesi için bir Microsoft Office Word belgesi veya Microsoft Office Excel çalışma sayfası üzerinde Windows Forms denetimleri ve *konak denetimleri* bağlayabilirsiniz. Her iki uygulama düzeyi ve belge düzeyi projesinde, denetimlere veri bağlayabilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Konak denetimleri Word ve Excel nesne modelleriyle, Word 'deki içerik denetimleri ve Excel 'de adlandırılmış aralıklar gibi nesneleri genişletir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

 Hem Windows Forms hem de konak denetimleri, hem *basit veri bağlamayı* hem de veri kümeleri ve veri tabloları gibi veri kaynaklarına *karmaşık veri bağlamayı* destekleyen Windows Forms veri bağlama modelini kullanır. Windows Forms veri bağlama modeli hakkında tüm bilgiler için bkz. [veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms).

## <a name="simple-data-binding"></a>Basit veri bağlama
 Basit veri bağlama, bir denetim özelliği bir veri tablosundaki değer gibi tek bir veri öğesine bağlandığında oluşur. Örneğin, denetimin bir <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> veri kümesindeki bir alana bağlanabilen bir özelliği vardır. Veri kümesindeki alanı değiştiğinde, adlandırılmış aralıktaki değeri de değişir. Denetim haricinde tüm konak denetimleri, <xref:Microsoft.Office.Tools.Word.XMLNodes> basit veri bağlamayı destekler. <xref:Microsoft.Office.Tools.Word.XMLNodes>Denetim bir koleksiyondur ve bu nedenle veri bağlamayı desteklemez.

 Bir konak denetimine basit veri bağlama gerçekleştirmek için, <xref:System.Windows.Forms.Binding> `DataBindings` denetimin özelliğine bir ekleyin. <xref:System.Windows.Forms.Binding>Nesnesi, denetimin özellik değeri ve bir veri öğesinin değeri arasındaki basit bağlamayı temsil eder.

 Aşağıdaki örnek, <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> özelliğinin belge düzeyindeki bir projedeki bir veri öğesine nasıl bağlanacağını gösterir.

 [!code-vb[Trin_BindableComponent#4](../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb#4)]
 [!code-csharp[Trin_BindableComponent#4](../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs#4)]

 Basit veri bağlamayı gösteren izlenecek yollar için bkz. Izlenecek yol: belge düzeyindeki bir proje için [belge düzeyi projede basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) ve bir VSTO eklentisi PROJESI Için [VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) .

## <a name="complex-data-binding"></a>Karmaşık veri bağlama
 Bir denetim özelliği bir veri tablosunda birden çok sütun gibi birden fazla veri öğesine bağlandığında, karmaşık veri bağlama bulunur. <xref:Microsoft.Office.Tools.Excel.ListObject>Excel için denetim, karmaşık veri bağlamayı destekleyen tek konak denetimidir. Denetim gibi karmaşık veri bağlamayı destekleyen birçok Windows Forms denetimi de vardır <xref:System.Windows.Forms.DataGridView> .

 Karmaşık veri bağlamayı gerçekleştirmek için `DataSource` denetimin özelliğini karmaşık veri bağlama tarafından desteklenen bir veri kaynağı nesnesi olarak ayarlayın. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> <xref:Microsoft.Office.Tools.Excel.ListObject> denetimin özelliği bir veri tablosunda birden çok sütuna bağlanabilir. Veri tablosundaki tüm veriler <xref:Microsoft.Office.Tools.Excel.ListObject> denetimde görünür ve veri tablosundaki veriler değiştikçe <xref:Microsoft.Office.Tools.Excel.ListObject> de değişir. Karmaşık veri bağlama için kullanabileceğiniz veri kaynaklarının bir listesi için, bkz. [Windows Forms tarafından desteklenen veri kaynakları](/dotnet/framework/winforms/data-sources-supported-by-windows-forms).

 Aşağıdaki kod örneği, <xref:System.Data.DataSet> iki nesne ile bir oluşturur <xref:System.Data.DataTable> ve tablolardan birini verilerle doldurur. Kodu daha sonra <xref:Microsoft.Office.Tools.Excel.ListObject> verileri içeren tabloya bağlar. Bu örnek, Excel belge düzeyi projesi içindir.

 [!code-csharp[Trin_ExcelListObject#18](../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs#18)]
 [!code-vb[Trin_ExcelListObject#18](../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb#18)]

 Karmaşık veri bağlamayı gösteren izlenecek yollar için bkz. Izlenecek yol: belge düzeyindeki bir proje için [belge düzeyi projede karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) ve bir VSTO eklentisi PROJESI Için [VSTO eklenti projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) .

## <a name="display-data-in-documents-and-workbooks"></a>Belgelerde ve çalışma kitaplarında verileri görüntüleme
 Belge düzeyi projelerde, veri **kaynakları** penceresini kullanarak belgelerinize veya çalışma kitaplarınıza veri bağlantılı denetimleri, Windows Forms için kullandığınız şekilde kolayca ekleyebilirsiniz. **Veri kaynakları** penceresini kullanma hakkında daha fazla bilgi için bkz. [Visual Studio 'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ve [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

### <a name="drag-controls-from-the-data-sources-window"></a>Denetimleri veri kaynakları penceresinden sürükleyin
 **Veri kaynakları** penceresinden bir nesne üzerine sürüklediğinizde belge üzerinde bir denetim oluşturulur. Oluşturulan denetimin türü, tek bir veri sütununu veya birden çok veri sütununu bağladığınıza bağlıdır.

 Excel 'de, <xref:Microsoft.Office.Tools.Excel.NamedRange> her bir alan için çalışma sayfasında bir denetim oluşturulur ve <xref:Microsoft.Office.Tools.Excel.ListObject> birden çok satır ve sütun içeren her bir veri aralığı için bir denetim oluşturulur. Bu varsayılanı, **veri kaynakları** penceresinde tablo veya alanı seçerek ve ardından açılan listeden farklı bir denetim seçerek değiştirebilirsiniz.

 <xref:Microsoft.Office.Tools.Word.ContentControl>Belgelere bir denetim eklenir. İçerik denetiminin türü, seçtiğiniz alanın veri türüne bağlıdır.

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

 Basit veri bağlamayı etkinleştiren konak denetimlerinden bir veri kaynağını güncelleştirmek için, çözümünüz bir tane kullanıyorsa bellek içi veri kaynağına ( <xref:System.Data.DataSet> veya gibi <xref:System.Data.DataTable> ) ve arka uç veritabanına güncelleştirmeleri göndermeniz gerekir.

 Denetimi kullanarak karmaşık veri bağlama gerçekleştirdiğinizde bellek içi veri kaynağını açıkça güncelleştirmeniz gerekmez <xref:Microsoft.Office.Tools.Excel.ListObject> . Bu durumda, değişiklikler ek kod olmadan bellek içi veri kaynağına otomatik olarak gönderilir.

 Daha fazla bilgi için bkz. [nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Nasıl yapılır: bir Windows formunda basit bağlantılı denetim oluşturma](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Önbellek verileri](../vsto/caching-data.md)
- [Office çözümlerindeki veriler](../vsto/data-in-office-solutions.md)

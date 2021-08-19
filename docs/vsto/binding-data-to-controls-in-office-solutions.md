---
title: Veri çözümlerinin denetimlerini Office bağlama
description: Microsoft Office Word belgesinde Windows Forms denetimlerini veya çalışma sayfasını bir veri kaynağına Excel nasıl bağlayabilirsiniz?
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
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: 41823c40520752366f0709b2e5772585ea10196a
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122059887"
---
# <a name="bind-data-to-controls-in-office-solutions"></a>Veri çözümlerinin denetimlerini Office bağlama
  Microsoft Office Word Windows form denetimlerini ve konak denetimlerini bir Microsoft Office Excel veri kaynağına bağlayacak ve böylece denetimler verileri otomatik olarak görüntüleyebilirsiniz.  Hem uygulama düzeyinde hem de belge düzeyindeki projelerde verileri denetimlere bekleyebilirsiniz.

 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]

 Konak denetimleri, Word'de yer alan nesneleri genişlet Excel word'de içerik denetimleri ve word'de adlandırılmış aralıklar gibi Excel. Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

 Hem Windows Forms hem de konak denetimleri, veri kümeleri ve veri  tabloları gibi  veri kaynaklarına basit veri bağlamayı ve karmaşık veri bağlamayı destekleyen Windows Forms veri bağlama modelini kullanır. Windows Forms'daki veri bağlama modeli hakkında tam bilgi için bkz. Veri [bağlama ve Windows Forms.](/dotnet/framework/winforms/data-binding-and-windows-forms)

## <a name="simple-data-binding"></a>Basit veri bağlama
 Bir denetim özelliği, veri tablodaki değer gibi tek bir veri öğesine bağlı olduğunda basit veri bağlaması vardır. Örneğin, <xref:Microsoft.Office.Tools.Excel.NamedRange> denetimin bir <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> veri kümesinde bir alana bağlanan bir özelliği vardır. Veri kümesinde alan değişti mi, adlandırılmış aralıkta değer de değişir. Denetim dışındaki tüm konak denetimleri <xref:Microsoft.Office.Tools.Word.XMLNodes> basit veri bağlamayı destekler. Denetim <xref:Microsoft.Office.Tools.Word.XMLNodes> bir koleksiyondur ve bu nedenle veri bağlamayı desteklemez.

 Bir konak denetimine basit veri bağlaması gerçekleştirmek için <xref:System.Windows.Forms.Binding> denetimin `DataBindings` özelliğine bir ekleyin. Nesne, <xref:System.Windows.Forms.Binding> denetimin özellik değeri ile veri öğesinin değeri arasındaki basit bağlamayı temsil eder.

 Aşağıdaki örnek, özelliğin belge düzeyi <xref:Microsoft.Office.Tools.Excel.NamedRange.Value2%2A> projedeki bir veri öğesine nasıl bağlanacağını gösterir.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_BindableComponent/Sheet1.vb" id="Snippet4":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_BindableComponent/Sheet1.cs" id="Snippet4":::

 Basit veri bağlamayı gösteren kılavuzlar için bkz. [Kılavuz:](../vsto/walkthrough-simple-data-binding-in-a-document-level-project.md) Belge düzeyi proje için belge düzeyinde bir projede basit veri bağlama ve [Kılavuz: VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md) Eklenti projesi için VSTO Eklenti projesinde basit veri bağlama.

## <a name="complex-data-binding"></a>Karmaşık veri bağlama
 Bir denetim özelliği, bir veri tablosunda birden çok sütun gibi birden fazla veri öğesine bağlı olduğunda karmaşık veri bağlaması vardır. Veri <xref:Microsoft.Office.Tools.Excel.ListObject> bağlama Excel, karmaşık veri bağlamayı destekleyen tek konak denetimidir. Denetim gibi karmaşık Windows destekleyen birçok Farklı Form denetimi de <xref:System.Windows.Forms.DataGridView> vardır.

 Karmaşık veri bağlaması gerçekleştirmek için denetimin özelliğini karmaşık veri `DataSource` bağlama tarafından desteklenen bir veri kaynağı nesnesine ayarlayın. Örneğin, <xref:Microsoft.Office.Tools.Excel.ListObject.DataSource%2A> denetimin özelliği <xref:Microsoft.Office.Tools.Excel.ListObject> bir veri tablosunda birden çok sütuna bağlı olabilir. Veri tablosunda yer alan tüm veriler denetimde görünür ve veri tablodaki <xref:Microsoft.Office.Tools.Excel.ListObject> veriler değiştiksinde de <xref:Microsoft.Office.Tools.Excel.ListObject> değişir. Karmaşık veri bağlama için kullanabileceğiniz veri kaynaklarının listesi için bkz. [Windows Forms tarafından desteklenen veri kaynakları.](/dotnet/framework/winforms/data-sources-supported-by-windows-forms)

 Aşağıdaki kod örneği iki <xref:System.Data.DataSet> nesneyle <xref:System.Data.DataTable> bir oluşturur ve tablolardan birini verilerle doldurmak için kullanılır. Kod daha sonra veri <xref:Microsoft.Office.Tools.Excel.ListObject> içeren tabloya bağlar. Bu örnek, belge Excel bir projeye örnektir.

 :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_ExcelListObject/Trin_ExcelListObject.cs" id="Snippet18":::
 :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_ExcelListObject/Sheet1.vb" id="Snippet18":::

 Karmaşık veri bağlamayı gösteren izlenecek yollar için [bkz.](../vsto/walkthrough-complex-data-binding-in-a-document-level-project.md) Belge düzeyi proje için belge düzeyinde bir projede karmaşık veri bağlama ve bir VSTO Eklenti projesi için [VSTO](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md) Eklenti projesinde karmaşık veri bağlama.

## <a name="display-data-in-documents-and-workbooks"></a>Belgelerde ve çalışma kitaplarında verileri görüntüleme
 Belge düzeyindeki projelerde Veri  Kaynakları penceresini kullanarak belgelerinize veya çalışma kitaplarınıza veriye bağlı denetimler ekleyebilirsiniz. Bu denetimler, belge veya Çalışma Kitapları için Windows kullanabilirsiniz. Veri Kaynakları penceresini kullanma hakkında daha **fazla** bilgi için bkz. [Windows Forms](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) denetimlerini Visual Studio veri kaynaklarına bağlama ve Yeni veri [kaynakları ekleme.](../data-tools/add-new-data-sources.md)

### <a name="drag-controls-from-the-data-sources-window"></a>Veri Kaynakları penceresinden denetimleri sürükleme
 Bir nesneyi Veri Kaynakları penceresinden üzerine sürüklerken belgede bir **denetim** oluşturulur. Oluşturulan denetim türü, tek bir veri sütununu mu yoksa birden çok veri sütununu mı bağlamaya bağlı olarak değişir.

 Daha Excel çalışma sayfasında tek tek her alan için bir denetim oluşturulur ve birden çok satır ve sütun içeren her veri aralığı <xref:Microsoft.Office.Tools.Excel.NamedRange> <xref:Microsoft.Office.Tools.Excel.ListObject> için bir denetim oluşturulur. Veri Kaynakları penceresinde tabloyu veya alanı ve  ardından açılan listeden farklı bir denetim seçerek bu varsayılan ayarı değiştirebilirsiniz.

 Belgelere <xref:Microsoft.Office.Tools.Word.ContentControl> bir denetim eklenir. İçerik denetimi türü, seçtiğiniz alanın veri türüne bağlıdır.

### <a name="bind-data-in-document-level-projects-at-design-time"></a>Tasarım zamanında belge düzeyi projelerde veri bağlama
 Aşağıdaki konular tasarım zamanında veri bağlama örneklerini gösterir:

- [Nasıl kullanılır: Çalışma sayfalarını bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)

- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)

- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)

- [Nasıl kullanılır: Belgeleri hizmetlerden gelen verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-services.md)

- [Nasıl kullanılır: Çalışma sayfasındaki veritabanı kayıtları arasında kaydırma](../vsto/how-to-scroll-through-database-records-in-a-worksheet.md)

### <a name="bind-data-in-vsto-add-in-projects"></a>Eklenti projelerinde VSTO bağlama
 Diğer VSTO projelerinde, yalnızca çalışma zamanında denetimler eklersiniz. Aşağıdaki konular çalışma zamanında veri bağlama örneklerini gösterir:

- [Adım adım kılavuz: Eklenti projesinde VSTO basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md)

- [Adım adım kılavuz: Eklenti projesinde VSTO karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="update-data-that-is-bound-to-host-controls"></a>Konak denetimlerine bağlı verileri güncelleştirme
 Veri kaynağı ile konak denetimi arasındaki veri bağlama işlemi, iki yollu bir veri güncelleştirmesi içerir. Basit veri bağlamada, veri kaynağında yapılan değişiklikler konak denetimine otomatik olarak yansıtılır, ancak konak denetiminde yapılan değişiklikler, veri kaynağını güncelleştirmek için açık bir çağrı gerektirir. Bunun nedeni, bazı durumlarda bir veriye bağlı alanda yapılan değişikliklerin başka bir veriye bağlı alanda yapılan değişikliklerle birlikte kabul edilmediğidir. Örneğin, biri yaş, biri de yıllara özel deneyim olmak için olmak için iki alanız olabilir. Deneyim yaşı aşamaz. Kullanıcı 50'den 25'e kadar olan yaşı ve ardından aynı anda değişiklik olmadığı sürece 30 ile 10 arasında bir deneyimi güncelleştirememektedir. Bu sorunu çözmek için, güncelleştirmeler kod tarafından açıkça gönderilene kadar basit veri bağlaması olan alanlar güncelleştirilmez.

 Basit veri bağlamayı etkinleştiren konak denetimlerinden bir veri kaynağını güncelleştirmek için, çözümünüz kullanıyorsa, güncelleştirmeleri bellek içinde veri kaynağına (veya gibi) ve arka uç veritabanına <xref:System.Data.DataSet> <xref:System.Data.DataTable> göndermeniz gerekir.

 Denetimi kullanarak karmaşık veri bağlama işlemi gerçekleştirecek olursanız bellek içinde veri kaynağını açıkça güncelleştirmeniz <xref:Microsoft.Office.Tools.Excel.ListObject> gerekmez. Bu durumda, değişiklikler ek kod olmadan bellek içinde veri kaynağına otomatik olarak gönderilir.

 Daha fazla bilgi için, [bkz. How to: Update a data source with data from a host control](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Veri bağlama ve Windows Forms](/dotnet/framework/winforms/data-binding-and-windows-forms)
- [Nasıl olur: Windows Form üzerinde basit bir Windows oluşturma](/dotnet/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Verileri yeniden veritabanına kaydetme](../data-tools/save-data-back-to-the-database.md)
- [TableAdapter kullanarak verileri güncelleştirme](../data-tools/update-data-by-using-a-tableadapter.md)
- [Önbellek verileri](../vsto/caching-data.md)
- [Veri Office verileri](../vsto/data-in-office-solutions.md)

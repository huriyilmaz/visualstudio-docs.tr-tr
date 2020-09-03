---
title: 'Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma'
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets [Office development in Visual Studio], populating
- databases [Office development in Visual Studio], populating worksheets
- data [Office development in Visual Studio], adding to worksheets
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 1b594014b2564b5730c1895a007294ee66e07637
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "85520126"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma

Belge düzeyindeki Office projelerinin verilerine Windows Forms projelerindeki verilere erişirken aynı şekilde erişebilirsiniz. Verileri çözümünüze getirmek için aynı araçları ve kodu kullanırsınız, hatta verileri görüntülemek için Windows Forms denetimleri de kullanabilirsiniz. Ayrıca, Microsoft Office Excel 'de olaylar ve veri bağlama özelliğiyle geliştirilmiş yerel nesneler olan konak denetimleri adlı denetimlerden yararlanabilirsiniz. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Aşağıdaki örnek, tasarımcı kullanarak belge düzeyi projelerde veri bağlantılı denetimlerin nasıl ekleneceğini gösterir. Çalışma zamanında uygulama düzeyi projelerde veriye bağlama denetimleri ekleme hakkında bir örnek için bkz. [Izlenecek yol: VSTO eklentisi projesinde karmaşık veri bağlama](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md).

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Tasarım zamanında çalışma sayfasına veri bağlantılı denetim ekleme

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Çalışma sayfasını bir veritabanındaki verilerle doldurmak için

1. Visual Studio 'da çalışma sayfası tasarımcıda açık olan bir Excel belge düzeyi projesi açın.

2. **Veri kaynakları** penceresini açın ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. **Veri kaynakları** penceresinden istediğiniz alanı veya tabloyu çalışma sayfanıza sürükleyin.

Çalışma sayfasında aşağıdaki denetimlerden biri oluşturuldu:

- Bir alanı sürüklerseniz, <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasında bir denetim oluşturulur. Daha fazla bilgi için bkz. [NamedRange denetimi](../vsto/namedrange-control.md).

- Bir tablo sürüklerseniz, <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasında bir denetim oluşturulur. Daha fazla bilgi için bkz. [ListObject denetimi](../vsto/listobject-control.md).

**Veri kaynakları** penceresinde tablo veya alanı seçerek ve ardından açılan listeden farklı bir denetim seçerek farklı bir denetim ekleyebilirsiniz.

## <a name="objects-in-the-project"></a>Projedeki nesneler

Denetime ek olarak, aşağıdaki verilerle ilgili nesneler projenize otomatik olarak eklenir:

- Veritabanına bağladığınız veri tablolarını kapsülleyen türü belirtilmiş bir veri kümesi. Daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

- <xref:System.Windows.Forms.BindingSource>Denetimi türü belirtilmiş veri kümesine bağlayan bir. Daha fazla bilgi için bkz. [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Türü belirtilmiş veri kümesini veritabanına bağlayan bir TableAdapter. Daha fazla bilgi için bkz. [TableAdapter Overview](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview).

- Hiyerarşik güncelleştirmeleri etkinleştirmek için veri kümesindeki tablo bağdaştırıcılarını koordine etmek üzere kullanılan bir TableAdapterManager. Daha fazla bilgi için bkz. [sıradüzensel Update](../data-tools/hierarchical-update.md) ve [TableAdapterManager Reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Projeyi çalıştırdığınızda, denetim veri kaynağındaki ilk kaydı görüntüler. <xref:System.Windows.Forms.BindingSource>Kullanıcıların kayıtlarda gezinme özelliğini etkinleştirmek için kullanabilirsiniz.

### <a name="to-scroll-through-the-records"></a>Kayıtlar arasında gezinmek için

- <xref:System.Windows.Forms.BindingSource>Ve gibi yöntemleri kullanın <xref:System.Windows.Forms.BindingSource.MoveNext%2A> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> .

Yazılan veri kümesine ve veritabanına güncelleştirmelerin gönderilmesi hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
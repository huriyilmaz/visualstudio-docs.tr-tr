---
title: 'Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 907b3deeadd0a56f9e47a6e17a40579a0c9ffa64
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985878"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma

Microsoft Office, Windows Forms projelerindeki verilere erişirken kullandığınız şekilde, belge düzeyi projelerdeki verilere erişebilirsiniz. Aynı araçları ve kodu kullanarak verileri bir veritabanından çözümünüze taşıyın ve verileri görüntülemek için Windows Forms denetimleri kullanabilirsiniz.

Bunlara ek olarak, konak denetimlerini kullanarak verileri görüntüleyebilirsiniz. Konak denetimleri, Microsoft Office Word 'de olaylar ve veri bağlama özelliğiyle geliştirilmiş yerel nesnelerdir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Aşağıdaki örnek, tasarımcı kullanarak belge düzeyi projelerde veri bağlantılı denetimlerin nasıl ekleneceğini gösterir. Çalışma zamanında VSTO eklenti projelerinde veriye bağlama denetimleri ekleme hakkında bir örnek için bkz. [Izlenecek yol: VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") İlgili video gösterimi için bkz. [Office sistemi için Visual Studio araçları kullanarak verileri Word 2007 içerik denetimlerine bağlama (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Belgeye tasarım zamanında bir denetim ekleme

### <a name="to-populate-a-document-with-data-from-a-database"></a>Belgeyi bir veritabanındaki verilerle doldurmak için

1. Belgeyi tasarımcıda açık olacak şekilde [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)]bir Word belge düzeyi projesi açın.

2. **Veri kaynakları** penceresini açın ve veritabanından bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. **Veri kaynakları** penceresinden istediğiniz alanı belgenize sürükleyin.

Belgeye bir içerik denetimi eklenir. İçerik denetiminin türü, seçtiğiniz alanın veri türüne bağlıdır. Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

**Veri kaynakları** penceresinde veri alanını seçip açılan listeden farklı bir denetim seçerek farklı bir denetim ekleyebilirsiniz.

## <a name="objects-in-the-project"></a>Projedeki nesneler

Denetime ek olarak, aşağıdaki verilerle ilgili nesneler projenize otomatik olarak eklenir:

- Veritabanına bağladığınız veri tablolarını kapsülleyen türü belirtilmiş bir veri kümesi. Daha fazla bilgi için bkz. [Visual Studio 'Da veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

- Denetimi türü belirtilmiş veri kümesine bağlayan bir <xref:System.Windows.Forms.BindingSource>. Daha fazla bilgi için bkz. [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Türü belirtilmiş veri kümesini veritabanına bağlayan bir TableAdapter. Daha fazla bilgi için bkz. [TableAdapters oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md).

- Hiyerarşik güncelleştirmeleri etkinleştirmek için veri kümesindeki tablo bağdaştırıcılarını koordine etmek üzere kullanılan bir TableAdapterManager. Daha fazla bilgi için bkz. [sıradüzensel Update](../data-tools/hierarchical-update.md) ve [TableAdapterManager Reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Projeyi çalıştırdığınızda, denetim veri kaynağındaki ilk kaydı görüntüler. Kullanıcıların kayıtlarda gezinme olanağı sağlamak için <xref:System.Windows.Forms.BindingSource> kullanabilirsiniz.

### <a name="to-scroll-through-the-records"></a>Kayıtlar arasında gezinmek için

- <xref:System.Windows.Forms.BindingSource.MoveNext%2A> ve <xref:System.Windows.Forms.BindingSource.MovePrevious%2A>gibi <xref:System.Windows.Forms.BindingSource> yöntemler kullanın.

Yazılan veri kümesine ve veritabanına güncelleştirmelerin gönderilmesi hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)
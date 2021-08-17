---
title: 'Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma'
description: çözümünüzdeki veritabanından verileri nasıl kullanabileceğinizi ve verileri bir belgede göstermek için Windows Forms denetimleri nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents, populating with data
- data, adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: ef324d108a8b8014c2c45671435ff2de811db6a72c5ca5e287013b4668949ae7
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121424092"
---
# <a name="how-to-populate-documents-with-data-from-a-database"></a>Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma

Microsoft Office, Windows Forms projelerindeki verilere erişirken kullandığınız şekilde, belge düzeyi projelerdeki verilere erişebilirsiniz. aynı araçları ve kodu kullanarak verileri bir veritabanından çözümünüze taşıyın ve verileri görüntülemek için Windows Forms denetimleri kullanabilirsiniz.

Bunlara ek olarak, konak denetimlerini kullanarak verileri görüntüleyebilirsiniz. konak denetimleri, Microsoft Office Word 'de olaylar ve veri bağlama özelliğiyle geliştirilmiş yerel nesnelerdir. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_wdalldoc](../vsto/includes/appliesto-wdalldoc-md.md)]

Aşağıdaki örnek, tasarımcı kullanarak belge düzeyi projelerde veri bağlantılı denetimlerin nasıl ekleneceğini gösterir. çalışma zamanında VSTO eklenti projelerine veri bağlama denetimleri ekleme hakkında bir örnek için, bkz. [izlenecek yol: VSTO eklenti projesinde basit veri bağlama](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).

![video bağlantısı](../vsto/media/playvideo.gif "video bağlantısı") ilgili video gösterimi için bkz. [Office sistemi için Visual Studio Araçları kullanarak verileri Word 2007 içerik denetimlerine bağlama (3,0)](/previous-versions/office/developer/office-2007/bb967663(v=office.12)).

## <a name="add-a-control-to-a-document-at-design-time"></a>Belgeye tasarım zamanında bir denetim ekleme

### <a name="to-populate-a-document-with-data-from-a-database"></a>Belgeyi bir veritabanındaki verilerle doldurmak için

1. Belge düzeyinde bir proje açın [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ve belgeyi tasarımcıda açın.

2. **Veri kaynakları** penceresini açın ve veritabanından bir veri kaynağı oluşturun. Daha fazla bilgi için bkz. [yeni bağlantılar ekleme](../data-tools/add-new-connections.md).

3. **Veri kaynakları** penceresinden istediğiniz alanı belgenize sürükleyin.

Belgeye bir içerik denetimi eklenir. İçerik denetiminin türü, seçtiğiniz alanın veri türüne bağlıdır. Daha fazla bilgi için bkz. [içerik denetimleri](../vsto/content-controls.md).

**Veri kaynakları** penceresinde veri alanını seçip açılan listeden farklı bir denetim seçerek farklı bir denetim ekleyebilirsiniz.

## <a name="objects-in-the-project"></a>Projedeki nesneler

Denetime ek olarak, aşağıdaki verilerle ilgili nesneler projenize otomatik olarak eklenir:

- Veritabanına bağladığınız veri tablolarını kapsülleyen türü belirtilmiş bir veri kümesi. Daha fazla bilgi için bkz. [Visual Studio veri kümesi araçları](../data-tools/dataset-tools-in-visual-studio.md).

- <xref:System.Windows.Forms.BindingSource>Denetimi türü belirtilmiş veri kümesine bağlayan bir. Daha fazla bilgi için bkz. [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview).

- Türü belirtilmiş veri kümesini veritabanına bağlayan bir TableAdapter. Daha fazla bilgi için bkz. [TableAdapters oluşturma ve yapılandırma](../data-tools/create-and-configure-tableadapters.md).

- Hiyerarşik güncelleştirmeleri etkinleştirmek için veri kümesindeki tablo bağdaştırıcılarını koordine etmek üzere kullanılan bir TableAdapterManager. Daha fazla bilgi için bkz. [sıradüzensel Update](../data-tools/hierarchical-update.md) ve [TableAdapterManager Reference](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference).

Projeyi çalıştırdığınızda, denetim veri kaynağındaki ilk kaydı görüntüler. <xref:System.Windows.Forms.BindingSource>Kullanıcıların kayıtlarda gezinme özelliğini etkinleştirmek için kullanabilirsiniz.

### <a name="to-scroll-through-the-records"></a>Kayıtlar arasında gezinmek için

- <xref:System.Windows.Forms.BindingSource>Ve gibi yöntemleri kullanın <xref:System.Windows.Forms.BindingSource.MoveNext%2A> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> .

Yazılan veri kümesine ve veritabanına güncelleştirmelerin gönderilmesi hakkında daha fazla bilgi için bkz. [nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
- [Office çözümlerinde yerel veritabanı dosyalarını kullanma genel bakış](../vsto/using-local-database-files-in-office-solutions-overview.md)
- [BindingSource Bileşenine Genel Bakış](/dotnet/framework/winforms/controls/bindingsource-component-overview)
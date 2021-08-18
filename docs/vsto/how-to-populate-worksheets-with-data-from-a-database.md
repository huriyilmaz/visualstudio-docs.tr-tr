---
title: 'Nasıl kullanılır: Çalışma sayfalarını veritabanındaki verilerle doldurmak'
description: Çözümünüzde bir nesneden verileri nasıl kullanabileceğinizi ve verileri bir çalışma sayfasında görüntülemek için Windows Forms denetimlerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: cd48feecfd100fc54748511107094bf1351c8c4d
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122046785"
---
# <a name="how-to-populate-worksheets-with-data-from-a-database"></a>Nasıl kullanılır: Çalışma sayfalarını veritabanındaki verilerle doldurmak

Belge düzeyindeki verilere, Office Forms projelerinde verilere erişen Windows erişebilirsiniz. Verileri çözümünüze getirmek için aynı araçları ve kodu kullanır ve hatta verileri görüntülemek için Windows Forms denetimlerini kullanabilirsiniz. Buna ek olarak, olaylar ve veri bağlama özelliğiyle geliştirilmiş olan Microsoft Office Excel yerel nesneler olan konak denetimleri olarak adlandırılan denetimlerden de faydalanabilirsiniz. Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

[!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]

Aşağıdaki örnek, bir tasarımcı kullanarak belge düzeyi projelerde veriye bağlı denetimlerin nasıl ekli olduğunu gösterir. Çalışma zamanında uygulama düzeyindeki projelerde veriye bağlı denetimler ekleme örneği için bkz. Adım adım: Eklenti projesinde [VSTO veri bağlama.](../vsto/walkthrough-complex-data-binding-in-vsto-add-in-project.md)

## <a name="add-a-data-bound-control-to-a-worksheet-at-design-time"></a>Tasarım zamanında çalışma sayfasına veriye bağlı denetim ekleme

### <a name="to-populate-a-worksheet-with-data-from-a-database"></a>Çalışma sayfasını veritabanındaki verilerle doldurmak için

1. Çalışma Excel tasarımcıda açık olacak şekilde Visual Studio düzeyinde bir proje açın.

2. Veri **Kaynakları penceresini** açın ve projeniz için bir veri kaynağı oluşturun. Daha fazla bilgi için [bkz. Yeni bağlantı ekleme.](../data-tools/add-new-connections.md)

3. Veri Kaynakları penceresinden istediğiniz alanı **veya tabloyu** çalışma sayfanıza sürükleyin.

Çalışma sayfasında aşağıdaki denetimlerden biri oluşturulur:

- Bir alanı sürüklersiniz, <xref:Microsoft.Office.Tools.Excel.NamedRange> çalışma sayfasında bir denetim oluşturulur. Daha fazla bilgi için bkz. [NamedRange denetimi.](../vsto/namedrange-control.md)

- Bir tabloyu sürüklersiniz, <xref:Microsoft.Office.Tools.Excel.ListObject> çalışma sayfasında bir denetim oluşturulur. Daha fazla bilgi için bkz. [ListObject denetimi.](../vsto/listobject-control.md)

Veri Kaynakları penceresindeki tabloyu veya alanı seçerek ve ardından açılan listeden farklı bir denetim seçerek farklı bir denetim ekleyebilirsiniz. 

## <a name="objects-in-the-project"></a>Projedeki nesneler

Denetime ek olarak, aşağıdaki veriyle ilgili nesneler projenize otomatik olarak eklenir:

- Veritabanında bağlı olduğunu veri tablolarını kapsüller türü türü bir veri kümesi. Daha fazla bilgi için [bkz. Visual Studio.](../data-tools/dataset-tools-in-visual-studio.md)

- Denetimi <xref:System.Windows.Forms.BindingSource> türüne sahip veri kümesine bağlayan bir. Daha fazla bilgi için bkz. [BindingSource bileşenine genel bakış.](/dotnet/framework/winforms/controls/bindingsource-component-overview)

- Türü doğru olan veri kümelerini veritabanına bağlayan tableAdapter. Daha fazla bilgi için bkz. [TableAdapter'a genel bakış.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadapter-overview)

- Hiyerarşik güncelleştirmeleri etkinleştirmek için veri kümesinde tablo bağdaştırıcılarını koordine etmek için kullanılan TableAdapterManager. Daha fazla bilgi için [bkz. Hiyerarşik güncelleştirme ve](../data-tools/hierarchical-update.md) [TableAdapterManager başvurusu.](../data-tools/fill-datasets-by-using-tableadapters.md#tableadaptermanager-reference)

Projeyi çalıştırarak denetim, veri kaynağında ilk kaydı görüntüler. Kullanıcıların kayıtları <xref:System.Windows.Forms.BindingSource> kaydırmalarını sağlamak için kullanabilirsiniz.

### <a name="to-scroll-through-the-records"></a>Kayıtlar arasında kaydırma yapmak için

- ve <xref:System.Windows.Forms.BindingSource> gibi yöntemleri <xref:System.Windows.Forms.BindingSource.MoveNext%2A> <xref:System.Windows.Forms.BindingSource.MovePrevious%2A> kullanın.

Türü türüne sahip veri kümesine ve veritabanına güncelleştirme gönderme hakkında bilgi için bkz. Nasıl güncelleştirmesi: Bir veri kaynağını bir konak [denetiminden alınan verilerle güncelleştirme.](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri hizmetlerden gelen verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-services.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
---
title: 'Nasıl kullanılır: Belgeleri hizmetlerden gelen verilerle doldurmak'
description: Çözümünüzde hizmetlerden gelen verileri nasıl kullanabileceğinizi ve verileri bir belgede görüntülemek için Windows Forms denetimlerini nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: office-development
ms.workload:
- office
ms.openlocfilehash: e68795d79b3cbd0bc190bc174200b90b3676779b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122155986"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Nasıl kullanılır: Belgeleri hizmetlerden gelen verilerle doldurmak

Veri erişimi, formlar için belge düzeyi projelerde Microsoft Office Formlar projelerinde olduğu Windows çalışır. Verileri çözümünüze getirmek için aynı araçları ve kodu kullanır ve hatta verileri görüntülemek için Windows Forms denetimlerini kullanabilirsiniz. Ayrıca, olaylar ve veri bağlama özelliğiyle geliştirilmiş olan Microsoft Office Excel ve Microsoft Office Word'de yerel nesneler olan konak denetimleri olarak adlandırılan denetimlerden de faydalanabilirsiniz. Daha fazla bilgi için [bkz. Konak öğelerine ve konak denetimlerine genel bakış.](../vsto/host-items-and-host-controls-overview.md)

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Aşağıdaki örnekte, tasarım zamanında belgelere veriye bağlı denetimlerin nasıl ekli olduğu gösterir. Çalışma zamanında VSTO Eklentileri'ne veriye bağlı denetimler ekleme örneği için bkz. Adım adım: Eklenti projesinde bir [hizmetten VSTO bağlama.](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md)

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Belge düzeyi projeyi web hizmetlerinden verilerle doldurmak için

1. Veri **Kaynakları penceresini açın** ve projeniz için bir hizmet veri kaynağı oluşturun. Daha fazla bilgi için [bkz. Yeni veri kaynakları ekleme.](../data-tools/add-new-data-sources.md)

2. Veri Kaynakları penceresinden istediğiniz **tabloyu veya alanı** belgenize sürükleyin.

     Belgede bir denetim oluşturulur, projenizin nesne sınıfına bağlı olan bir oluşturulur <xref:System.Windows.Forms.BindingSource> ve hizmet için sınıflar oluşturulur.

3. Kodunda, 1. adımda bağlandıktan sonra web hizmeti sınıfının bir örneğini oluşturun.

4. Web hizmetiyle iletişim için gerekli özellikler varsa, bu özelliklerin örneklerini oluşturun.

5. Web hizmeti tarafından ortaya atılan yöntemleri ve 4. adımda oluşturduğunuz tüm özellik örneklerini kullanarak veri isteği oluşturun ve gönderin.

     Kullandığınız yöntemler, web hizmetinin sunduğu hizmetlere bağlıdır.

6. Web hizmetlerinden gelen veri yanıtını <xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğinin özelliğine attayabilirsiniz. <xref:System.Windows.Forms.BindingSource>

Projeyi çalıştırarak denetimler veri kaynağında ilk kaydı görüntüler. içinde nesneleri kullanarak para birimi olaylarını işerek kayıtlar arasında kaydırmayı <xref:System.Windows.Forms.BindingSource> etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Veri çözümlerinin denetimlerini Office bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl kullanılır: Çalışma sayfalarını veritabanındaki verilerle doldurmak](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl kullanılır: Belgeleri nesnelerden verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl kullanılır: Belgeleri bir veritabanındaki verilerle doldurmak](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl kullanılır: Bir veri kaynağını konak denetiminden verilerle güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
---
title: 'Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- documents [Office development in Visual Studio], populating with data
- Web services [Office development in Visual Studio], populating documents
- data [Office development in Visual Studio], adding to documents
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 4f53000f7d6aa8bdd8261bbe5658607918b6b449
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/28/2019
ms.locfileid: "72985864"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma

Veri erişimi, Windows Forms projelerinde olduğu gibi Microsoft Office için belge düzeyi projelerde aynı şekilde çalışacaktır. Verileri çözümünüze getirmek için aynı araçları ve kodu kullanırsınız, hatta verileri görüntülemek için Windows Forms denetimleri de kullanabilirsiniz. Ayrıca, Microsoft Office Excel 'de yerel nesneler olan ve olaylar ve veri bağlama özelliğiyle geliştirilmiş Word Microsoft Office, ana bilgisayar denetimleri adlı denetimlerin avantajlarından yararlanabilirsiniz. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Aşağıdaki örnek, tasarım zamanında belgelere veriye dayalı denetimlerin nasıl ekleneceğini gösterir. Çalışma zamanında VSTO Eklentilerindeki veriye bağlı denetimlerin nasıl ekleneceği hakkında bir örnek için bkz. [Izlenecek yol: VSTO eklenti projesindeki bir hizmetten veriye bağlama](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Belge düzeyindeki bir projeyi bir Web hizmetindeki verilerle doldurmak için

1. **Veri kaynakları** penceresini açın ve projeniz için bir hizmet veri kaynağı oluşturun. Daha fazla bilgi için bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

2. **Veri kaynakları** penceresinden istediğiniz tabloyu veya alanı belgenize sürükleyin.

     Belgede bir denetim oluşturulur, projenizdeki nesne sınıfına bağlı bir <xref:System.Windows.Forms.BindingSource> oluşturulur ve hizmet için sınıflar oluşturulur.

3. Kodunuzda, 1. adımda ' ye bağladığınız Web hizmeti sınıfının bir örneğini oluşturun.

4. Web hizmetiyle iletişim için gereken özellikler varsa, bu özelliklerin örneklerini oluşturun.

5. Web hizmeti tarafından sunulan yöntemleri ve 4. adımda oluşturduğunuz tüm özellik örneklerini kullanarak bir veri isteği oluşturun ve gönderin.

     Kullandığınız yöntemler Web hizmetinin sunduğu yöntemlere bağlıdır.

6. Web hizmetinden veri yanıtını <xref:System.Windows.Forms.BindingSource><xref:System.Windows.Forms.BindingSource.DataSource%2A> özelliğine atayın.

Projeyi çalıştırdığınızda, denetimler veri kaynağındaki ilk kaydı görüntüler. <xref:System.Windows.Forms.BindingSource>nesneleri kullanarak para birimi olaylarını işleyerek kayıtlarda gezinmeyi etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde verileri denetimlere bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
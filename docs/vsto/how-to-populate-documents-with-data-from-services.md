---
title: 'Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma'
description: çözümünüzdeki hizmetlerden verileri nasıl kullanabileceğinizi ve verileri bir belgede göstermek için Windows Forms denetimlerini nasıl kullanabileceğinizi öğrenin.
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
ms.openlocfilehash: d8addba363743a59279e7b99cfa2b7f088b23ba8bf15a0b2f6917ed365f54962
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121243568"
---
# <a name="how-to-populate-documents-with-data-from-services"></a>Nasıl yapılır: belgeleri hizmetlerdeki verilerle doldurma

veri erişimi, Windows Forms projelerinde olduğu gibi Microsoft Office için belge düzeyi projelerde aynı şekilde çalışacaktır. verileri çözümünüze getirmek için aynı araçları ve kodu kullanırsınız, hatta verileri görüntülemek için Windows Forms denetimleri de kullanabilirsiniz. ayrıca, Microsoft Office Excel yerel nesneler olan ve olaylar ve veri bağlama özelliğiyle geliştirilmiş Word Microsoft Office olan konak denetimleri adlı denetimlerden faydalanabilirsiniz. Daha fazla bilgi için bkz. [konak öğeleri ve konak denetimlerine genel bakış](../vsto/host-items-and-host-controls-overview.md).

[!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

Aşağıdaki örnek, tasarım zamanında belgelere veriye dayalı denetimlerin nasıl ekleneceğini gösterir. çalışma zamanında VSTO eklentilerde veriye bağlı denetimler ekleme hakkında bir örnek için, bkz. [izlenecek yol: bir hizmetten verileri bir VSTO eklenti projesinde bağlama](../vsto/walkthrough-binding-to-data-from-a-service-in-a-vsto-add-in-project.md).

## <a name="to-populate-a-document-level-project-with-data-from-a-web-service"></a>Belge düzeyindeki bir projeyi bir Web hizmetindeki verilerle doldurmak için

1. **Veri kaynakları** penceresini açın ve projeniz için bir hizmet veri kaynağı oluşturun. Daha fazla bilgi için bkz. [Yeni veri kaynakları ekleme](../data-tools/add-new-data-sources.md).

2. **Veri kaynakları** penceresinden istediğiniz tabloyu veya alanı belgenize sürükleyin.

     Belge üzerinde bir denetim oluşturulur, <xref:System.Windows.Forms.BindingSource> projenizdeki nesne sınıfına bağlı olan bir oluşturulur ve hizmet için sınıflar oluşturulur.

3. Kodunuzda, 1. adımda ' ye bağladığınız Web hizmeti sınıfının bir örneğini oluşturun.

4. Web hizmetiyle iletişim için gereken özellikler varsa, bu özelliklerin örneklerini oluşturun.

5. Web hizmeti tarafından sunulan yöntemleri ve 4. adımda oluşturduğunuz tüm özellik örneklerini kullanarak bir veri isteği oluşturun ve gönderin.

     Kullandığınız yöntemler Web hizmetinin sunduğu yöntemlere bağlıdır.

6. Web hizmetinden veri yanıtını <xref:System.Windows.Forms.BindingSource.DataSource%2A> öğesinin özelliğine atayın <xref:System.Windows.Forms.BindingSource> .

Projeyi çalıştırdığınızda, denetimler veri kaynağındaki ilk kaydı görüntüler. İçindeki nesneleri kullanarak para birimi olaylarını işleyerek kayıtlar arasında kaydırma yapabilirsiniz <xref:System.Windows.Forms.BindingSource> .

## <a name="see-also"></a>Ayrıca bkz.

- [Office çözümlerinde denetimlere veri bağlama](../vsto/binding-data-to-controls-in-office-solutions.md)
- [Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)
- [Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)
- [Nasıl yapılır: çalışma sayfalarını bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-worksheets-with-data-from-a-database.md)
- [Nasıl yapılır: belgeleri nesnelerden verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-objects.md)
- [Nasıl yapılır: belgeleri bir veritabanındaki verilerle doldurma](../vsto/how-to-populate-documents-with-data-from-a-database.md)
- [Nasıl yapılır: bir konak denetimindeki verilerle veri kaynağını güncelleştirme](../vsto/how-to-update-a-data-source-with-data-from-a-host-control.md)
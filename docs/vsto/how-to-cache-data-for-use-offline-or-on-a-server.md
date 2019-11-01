---
title: 'Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma'
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- data caching [Office development in Visual Studio], server use
- Office applications [Office development in Visual Studio], data
- datasets [Office development in Visual Studio], caching
- offline data [Office development in Visual Studio]
- data [Office development in Visual Studio], caching
- data caching [Office development in Visual Studio], offline use
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 551d27cf8d40f2e6e9c996b031fa6c4e0a233355
ms.sourcegitcommit: 40bd5b27f247a07c2e2514acb293b23d6ce03c29
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/31/2019
ms.locfileid: "73189571"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma
  Çevrimdışı kullanılabilir olması için bir veri öğesini belgede önbelleğe alınacak şekilde işaretleyebilirsiniz. Bu, belge bir sunucuda depolandığında belgedeki verilerin diğer kodla değiştirilmesini de olanaklı kılar.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri öğesi kodunuzda bildirildiği sırada veya bir <xref:System.Data.DataSet>kullanıyorsanız, **Özellikler** penceresinde bir özelliği ayarlayarak önbelleğe alınacak bir veri öğesini işaretleyebilirsiniz. <xref:System.Data.DataSet> veya <xref:System.Data.DataTable>olmayan bir veri öğesini önbelleğe alırsanız, belgede önbelleğe alma ölçütlerini karşıladığından emin olun. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

> [!NOTE]
> **Önbelleğe alınmış** ve **WithEvents** olarak işaretlenen Visual Basic kullanılarak oluşturulan veri kümeleri ( **veri kaynakları** penceresinden veya **CacheInDocument** özelliği true olarak ayarlanan **araç kutusundan** sürüklenen veri kümeleri dahil)) önbellekte adlarının önüne bir alt çizgi sahiptir. Örneğin, bir veri kümesi oluşturup **müşterileri**olarak ayarlarsanız, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> adı önbellekteki **müşteriler** olur. Bu önbelleğe alınmış öğeye erişmek için <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> kullandığınızda, **müşteriler**yerine **_müşteriler** belirtmeniz gerekir.

### <a name="to-cache-data-in-the-document-using-code"></a>Kodu kullanarak belgedeki verileri önbelleğe almak için

1. Veri öğesi için, bir Word projesinde `ThisDocumen`t sınıfı veya bir Excel projesindeki `ThisWorkbook` sınıfı gibi, projenizdeki bir konak öğesi sınıfının bir üyesi olarak bir ortak alan veya özellik bildirin.

2. Veri öğesini belgenin veri önbelleğinde depolanacak şekilde işaretlemek için <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> özniteliğini üyeye uygulayın. Aşağıdaki örnek, bir <xref:System.Data.DataSet>için bu özniteliği bir alan bildirimine uygular.

     [!code-csharp[Trin_VstcoreDataExcel#11](../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb#11)]

3. Veri öğesinin bir örneğini oluşturmak için kod ekleyin ve varsa onu veritabanından yükleyin.

     Veri öğesi yalnızca ilk oluşturulduğunda yüklenir; Bundan sonra, önbellek belgeyle kalır ve güncelleştirmek için başka kod yazmanız gerekir.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Özellikler penceresi kullanarak belgedeki bir veri kümesini önbelleğe almak için

1. Visual Studio tasarımcısında araçları kullanarak veri kümesini projeye ekleyin, örneğin, **veri kaynakları** penceresini kullanarak projenize bir veri kaynağı ekleyin.

2. Henüz bir tane yoksa veri kümesinin bir örneğini oluşturun ve tasarımcıdaki örneği seçin.

3. **Özellikler** penceresinde **CacheInDocument** özelliğini **true**olarak ayarlayın.

     Daha fazla bilgi için bkz. [Office projelerindeki Özellikler](../vsto/properties-in-office-projects.md).

4. **Özellikler** penceresinde, **değiştiriciler** özelliğini **Public** (varsayılan olarak **dahili**) olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Sunucudaki belgelerdeki verilere erişin](../vsto/accessing-data-in-documents-on-the-server.md)
- [Verileri kaydetme](../data-tools/save-data-back-to-the-database.md)

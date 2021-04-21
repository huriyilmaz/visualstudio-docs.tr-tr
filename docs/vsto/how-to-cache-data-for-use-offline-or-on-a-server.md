---
title: 'Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma'
description: Çevrimdışı kullanılabilir olması için bir veri öğesini belgede önbelleğe alınacak şekilde işaretleyin. Bu, belgedeki verilerin diğer kodla değiştirilmesini olanaklı kılar.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
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
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 07d7a33d90fd9d05c041ddc27f92a5b6a59bb75e
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825998"
---
# <a name="how-to-cache-data-for-use-offline-or-on-a-server"></a>Nasıl yapılır: çevrimdışı veya sunucuda kullanmak üzere verileri önbelleğe alma
  Çevrimdışı kullanılabilir olması için bir veri öğesini belgede önbelleğe alınacak şekilde işaretleyebilirsiniz. Bu, belge bir sunucuda depolandığında belgedeki verilerin diğer kodla değiştirilmesini de olanaklı kılar.

 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]

 Veri öğesi kodunuzda bildirildiği sırada veya kullanıyorsanız, <xref:System.Data.DataSet> **Özellikler** penceresinde bir özellik ayarlayarak önbelleğe alınacak bir veri öğesini işaretleyebilirsiniz. Veya olmayan bir veri öğesini önbelleğe alırsanız <xref:System.Data.DataSet> <xref:System.Data.DataTable> , belgede önbelleğe alma ölçütlerini karşıladığından emin olun. Daha fazla bilgi için bkz. [önbelleği verileri](../vsto/caching-data.md).

> [!NOTE]
> **Önbelleğe alınmış** ve **WithEvents** olarak işaretlenen Visual Basic kullanılarak oluşturulan veri kümeleri ( **veri kaynakları** penceresinden veya **CacheInDocument** özelliği **true** olarak ayarlanan **araç kutusu** dahil), önbellekte adlarına önek eklenmiş bir alt çizgi vardır. Örneğin, bir veri kümesi oluşturup **müşterileri** olarak ayarlarsanız, <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> ad önbellekte **_Customers** olur. <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>Bu önbelleğe alınmış öğeye erişmek için kullandığınızda, **müşteriler** yerine **_Customers** belirtmeniz gerekir.

### <a name="to-cache-data-in-the-document-using-code"></a>Kodu kullanarak belgedeki verileri önbelleğe almak için

1. Projenizdeki bir konak öğesi sınıfının bir üyesi olarak veri öğesi için bir ortak alan veya özellik bildirin; Örneğin, `ThisDocumen` bir Word projesindeki t sınıfı veya bir `ThisWorkbook` Excel projesindeki sınıfı.

2. <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>Veri öğesini belgenin veri önbelleğinde depolanacak şekilde işaretlemek için özniteliği üyeye uygulayın. Aşağıdaki örnek, bu özniteliği bir için alan bildirimine uygular <xref:System.Data.DataSet> .

     :::code language="csharp" source="../vsto/codesnippet/CSharp/Trin_VstcoreDataExcelCS/Sheet1.cs" id="Snippet11":::
     :::code language="vb" source="../vsto/codesnippet/VisualBasic/Trin_VstcoreDataExcelVB/Sheet1.vb" id="Snippet11":::

3. Veri öğesinin bir örneğini oluşturmak için kod ekleyin ve varsa onu veritabanından yükleyin.

     Veri öğesi yalnızca ilk oluşturulduğunda yüklenir; Bundan sonra, önbellek belgeyle kalır ve güncelleştirmek için başka kod yazmanız gerekir.

### <a name="to-cache-a-dataset-in-the-document-by-using-the-properties-window"></a>Özellikler penceresi kullanarak belgedeki bir veri kümesini önbelleğe almak için

1. Visual Studio tasarımcısında araçları kullanarak veri kümesini projeye ekleyin, örneğin, **veri kaynakları** penceresini kullanarak projenize bir veri kaynağı ekleyin.

2. Henüz bir tane yoksa veri kümesinin bir örneğini oluşturun ve tasarımcıdaki örneği seçin.

3. **Özellikler** penceresinde **CacheInDocument** özelliğini **true** olarak ayarlayın.

     Daha fazla bilgi için bkz. [Office projelerindeki Özellikler](../vsto/properties-in-office-projects.md).

4. **Özellikler** penceresinde, **değiştiriciler** özelliğini **Public** (varsayılan olarak **dahili**) olarak ayarlayın.

## <a name="see-also"></a>Ayrıca bkz.
- [Önbellek verileri](../vsto/caching-data.md)
- [Nasıl yapılır: bir Office belgesinde program aracılığıyla veri kaynağını önbelleğe alma](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)
- [Nasıl yapılır: parola korumalı bir belgedeki verileri önbelleğe alma](../vsto/how-to-cache-data-in-a-password-protected-document.md)
- [Sunucudaki belgelerdeki verilere erişin](../vsto/accessing-data-in-documents-on-the-server.md)
- [Verileri kaydetme](../data-tools/save-data-back-to-the-database.md)

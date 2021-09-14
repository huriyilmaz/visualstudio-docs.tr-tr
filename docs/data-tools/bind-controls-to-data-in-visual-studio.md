---
title: Verilere denetimler bağlama
description: Denetimleri veri kaynağında Visual Studio. Veri Kaynakları penceresinden öğeleri sürükleyerek veriye bağlı denetimler oluşturun.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: adbe3262e1da3c0d28f16bf32d94952c6565e142
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631604"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere denetimler bağlama

Verileri denetimlere bağarak uygulamanın kullanıcılarına veri görüntüebilirsiniz. Veri Kaynakları penceresindeki öğeleri tasarım yüzeyine  veya veri kaynakları penceresindeki bir yüzeydeki denetimlere sürükleyerek bu veriye bağlı Visual Studio.

Bu konu başlığında, veriye bağlı denetimler oluşturmak için kullanabileceğiniz veri kaynakları açıklanmıştır. Ayrıca veri bağlamayla ilgili bazı genel görevleri de açıklar. Veriye bağlı denetimler oluşturma hakkında daha ayrıntılı bilgi için bkz. [Windows Forms](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) denetimlerini Visual Studio'de verilere bağlama ve [WPF](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)denetimlerini Visual Studio.

## <a name="data-sources"></a>Veri kaynakları

Veri bağlama bağlamında, veri kaynağı bellekte kullanıcı arabiriminize bağlanan verileri temsil eder. Pratikte veri kaynağı bir Entity Framework sınıfı, veri kümesi, bir .NET proxy nesnesi, bir LINQ to SQL sınıfı veya herhangi bir .NET nesnesi ya da koleksiyonunda kapsüllene bir hizmet uç noktası olabilir. Bazı veri kaynakları, öğeleri Veri Kaynakları penceresinden sürükleyerek veriye bağlı **denetimler** oluşturmanıza olanak sağlarken, diğer veri kaynakları bunu yapmaz. Aşağıdaki tabloda hangi veri kaynaklarının desteklen olduğu gösterir.

| Veri kaynağı | **Windows Forms Designer'da sürükleyip bırakma desteği** | WPF Tasarımcısı'nda **sürükle ve bırak desteği** | Silverlight Tasarımcısı'nda sürükle **ve bırak desteği** |
| - | - | - | - |
| Veri kümesi | Yes | Yes | Hayır |
| Varlık Veri Modeli | Evet<sup>1</sup> | Yes | Yes |
| LINQ to SQL sınıfları | <sup>Hayır 2</sup> | <sup>Hayır 2</sup> | <sup>Hayır 2</sup> |
| Hizmetler [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] (, WCF hizmetleri ve web hizmetleri dahil) | Yes | Yes | Yes |
| Nesne | Yes | Yes | Yes |
| SharePoint | Yes | Yes | Yes |

1. Varlık Veri Modeli **sihirbazını** kullanarak modeli oluşturma ve bu nesneleri tasarımcıya sürükleme.

2. LINQ to SQL sınıfları Veri Kaynakları **penceresinde** görünmez. Ancak, yeni sınıflara dayalı yeni bir nesne veri kaynağı LINQ to SQL ve ardından veriye bağlı denetimler oluşturmak için bu nesneleri tasarımcıya sürükleyebilirsiniz. Daha fazla bilgi için, [bkz. Walkthrough: Creating LINQ to SQL Classes (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Veri kaynakları projeniz için Veri Kaynakları penceresinde öğeler **olarak** kullanılabilir. Bu pencere, bir form tasarım yüzeyi projenizin etkin penceresi olduğunda görünür veya Diğer Veri Kaynaklarını Görüntüle'Windows seçerek bu  >    >  **pencereyi açabilirsiniz.** Bu penceredeki öğeleri sürükleyerek temel alınan verilere bağlı denetimler oluşturabilir ve sağ tıklayarak veri kaynaklarını yapılandırabilirsiniz.

![Veri Kaynakları penceresi](../data-tools/media/raddata-data-sources-window.png)

Veri Kaynakları penceresinde görüntülenen her veri **türü için,** öğeyi tasarımcıya sürüklerken bir varsayılan denetim oluşturulur. Veri Kaynakları penceresinden bir **öğeyi sürüklemeden** önce oluşturulan denetimi değiştirebilirsiniz. Daha fazla bilgi için [bkz. Veri Kaynakları penceresinden sürüklenrken oluşturulacak denetimi ayarlama.](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)

## <a name="tasks-involved-in-binding-controls-to-data"></a>Denetimler ile veri bağlamayla ilgili görevler

Aşağıdaki tabloda, verilere denetimler bağlamak için gerçekleştirilen en yaygın görevlerden bazıları listele türetir.

|Görev|Daha fazla bilgi|
|----------| - |
|Veri **Kaynakları penceresini** açın.|Düzenleyicide bir tasarım yüzeyi açın ve Veri Kaynaklarını  >  **Görüntüle'yi seçin.**|
|Projenize bir veri kaynağı ekleyin.|[Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)|
|Veri Kaynakları penceresinden tasarımcıya bir öğe sürüklerken **oluşturulan** denetimi ayarlayın.|[Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|Veri Kaynakları penceresindeki öğelerle ilişkili denetimlerin **listesini** değiştirme.|[Veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Veriye bağlı denetimler oluşturun.|[Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Bir nesne veya koleksiyona bağlama.|[Visual Studio'da nesne bağlama](../data-tools/bind-objects-in-visual-studio.md)|
|Kullanıcı arabiriminde görünen verileri filtrele.|[Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Denetimler için açıklamalı alt yazıları özelleştirme.|[Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Formlar veri bağlama](/dotnet/framework/winforms/windows-forms-data-binding)

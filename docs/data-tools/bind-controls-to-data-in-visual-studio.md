---
title: Denetimleri verilere bağlama
description: Denetimleri Visual Studio verilere bağlayın. Veri kaynakları penceresinden öğeleri sürükleyerek veri bağlantılı denetimler oluşturun.
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
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122081938"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere denetimler bağlama

Verileri denetimlere bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. **Veri kaynakları** penceresinden öğeleri Visual Studio bir yüzey üzerinde bir tasarım yüzeyine veya denetimlerine sürükleyerek, bu veriye bağlı denetimleri oluşturabilirsiniz.

Bu konuda, veri bağlantılı denetimler oluşturmak için kullanabileceğiniz veri kaynakları açıklanmaktadır. Ayrıca, Veri bağlamada yer alan genel görevlerden bazılarını açıklar. veriye bağlı denetimler oluşturma hakkında daha ayrıntılı bilgi için bkz. [Visual Studio içindeki verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ve [Visual Studio içindeki verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md).

## <a name="data-sources"></a>Veri kaynakları

Veri bağlama bağlamında, veri kaynağı, Kullanıcı arabiriminize bağlanabilen bellekteki verileri temsil eder. pratik koşullarda, bir veri kaynağı bir Entity Framework sınıfı, bir veri kümesi, bir .net proxy nesnesinde veya bir LINQ to SQL sınıfında veya herhangi bir .net nesne veya koleksiyonda kapsüllenmiş bir hizmet uç noktası olabilir. Bazı veri kaynakları, verileri **veri kaynakları** penceresinden sürükleyerek, diğer veri kaynakları olmasa da veri bağlantılı denetimler oluşturmanıza olanak sağlar. Aşağıdaki tabloda hangi veri kaynaklarının desteklendiği gösterilmektedir.

| Veri kaynağı | **Windows Form Tasarımcısı için** sürükle ve bırak desteği | **WPF Tasarımcısında** sürükle ve bırak desteği | **Silverlight tasarımcısında** sürükle ve bırak desteği |
| - | - | - | - |
| Veri kümesi | Yes | Yes | Hayır |
| Varlık Veri Modeli | Evet<sup>1</sup> | Yes | Yes |
| LINQ to SQL sınıfları | <sup>2</sup> yok | <sup>2</sup> yok | <sup>2</sup> yok |
| Hizmetler ( [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] WCF Hizmetleri ve Web Hizmetleri dahil) | Yes | Yes | Yes |
| Nesne | Yes | Yes | Yes |
| SharePoint | Yes | Yes | Yes |

1. **Varlık veri modeli** Sihirbazı 'nı kullanarak modeli oluşturun ve ardından bu nesneleri tasarımcıya sürükleyin.

2. LINQ to SQL sınıfları **veri kaynakları** penceresinde görünmez. ancak, LINQ to SQL sınıfları temel alan yeni bir nesne veri kaynağı ekleyebilirsiniz ve ardından bu nesneleri tasarımcıya sürükleyerek veriye bağlı denetimler oluşturabilirsiniz. daha fazla bilgi için bkz. [izlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md).

## <a name="data-sources-window"></a>Veri Kaynakları penceresi

Veri kaynakları, projenizde **veri kaynakları** penceresinde öğeler olarak kullanılabilir. bu pencere, form tasarım yüzeyi projenizdeki etkin pencere olduğunda görünür veya   >  **diğer Windows**  >  **veri kaynaklarını** görüntüle ' yi seçerek (proje açıkken) açabilirsiniz. Bu penceredeki öğeleri, temel alınan verilere bağlanan denetimler oluşturmak için sürükleyebilir ve sağ tıklayarak da veri kaynaklarını yapılandırabilirsiniz.

![Veri Kaynakları penceresi](../data-tools/media/raddata-data-sources-window.png)

**Veri kaynakları** penceresinde görüntülenen her veri türü için, öğeyi tasarımcıya sürüklediğinizde varsayılan bir denetim oluşturulur. Bir öğeyi **veri kaynakları** penceresinden sürüklemeden önce, oluşturulan denetimi değiştirebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Denetimlere veri bağlama ile ilgili görevler

Aşağıdaki tabloda, denetimleri verilere bağlamak için gerçekleştirdiğiniz en yaygın görevlerden bazıları listelenmektedir.

|Görev|Daha fazla bilgi|
|----------| - |
|**Veri kaynakları** penceresini açın.|Düzenleyicide bir tasarım yüzeyi açın ve   >  **veri kaynaklarını** görüntüle ' yi seçin.|
|Projenize bir veri kaynağı ekleyin.|[Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)|
|**Veri kaynakları** penceresinden tasarımcıya bir öğe sürüklediğinizde oluşturulan denetimi ayarlayın.|[Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|**Veri kaynakları** penceresindeki öğelerle ilişkili denetimlerin listesini değiştirin.|[Veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Veriye göre bağlantılı denetimler oluşturun.|[Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)|
|Bir nesne veya koleksiyona bağlayın.|[Visual Studio'da nesne bağlama](../data-tools/bind-objects-in-visual-studio.md)|
|Kullanıcı arabiriminde görünen verileri filtreleyin.|[Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Denetimler için açıklamalı alt yazıları özelleştirin.|[Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Ayrıca bkz.

- [.NET için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)
- [Windows Forms veri bağlama](/dotnet/framework/winforms/windows-forms-data-binding)

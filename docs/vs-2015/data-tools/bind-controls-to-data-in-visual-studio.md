---
title: Denetimleri verilere bağlama
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- data, displaying
- data sources, displaying data
- Data Sources window
- displaying data
ms.assetid: be8b6623-86a6-493e-ab7a-050de4661fd6
caps.latest.revision: 42
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 31e2086126e9a17554c80b53858205e83fd504fd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673044"
---
# <a name="bind-controls-to-data-in-visual-studio"></a>Visual Studio'da verilere denetimler bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Verileri denetimlere bağlayarak uygulamanızın kullanıcılarına verileri görüntüleyebilirsiniz. **Veri kaynakları** penceresinden öğeleri, Visual Studio 'daki bir yüzey üzerindeki bir tasarım yüzeyine veya denetimlerine sürükleyerek bu veriye bağlı denetimler oluşturabilirsiniz.

 Bu konuda, veri bağlantılı denetimler oluşturmak için kullanabileceğiniz veri kaynakları açıklanmaktadır. Ayrıca, Veri bağlamada yer alan genel görevlerden bazılarını açıklar. Veriye bağlı denetimler oluşturma hakkında daha ayrıntılı bilgi için bkz. [Visual Studio 'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md) ve [Visual STUDIO 'daki verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md).

## <a name="data-sources"></a>Veri kaynakları
 Veri bağlama bağlamında, veri kaynağı, Kullanıcı arabiriminize bağlanabilen bellekteki verileri temsil eder. Pratik koşullarda, bir veri kaynağı bir Entity Framework sınıfı, bir veri kümesi, bir .NET proxy nesnesinde veya bir LINQ to SQL sınıfında veya herhangi bir .NET nesne veya koleksiyonda kapsüllenmiş bir hizmet uç noktası olabilir. Bazı veri kaynakları, verileri **veri kaynakları** penceresinden sürükleyerek, diğer veri kaynakları olmasa da veri bağlantılı denetimler oluşturmanıza olanak sağlar. Aşağıdaki tabloda hangi veri kaynaklarının desteklendiği gösterilmektedir.

|Veri kaynağı|**Windows Form Tasarımcısı için** sürükle ve bırak desteği|**WPF Tasarımcısında** sürükle ve bırak desteği|**Silverlight tasarımcısında** sürükle ve bırak desteği|
|-----------------|---------------------------------------------------------------|-----------------------------------------------------|-------------------------------------------------------------|
|Veri kümesi|Evet|Evet|Hayır|
|Varlık Veri Modeli|Evet<sup>1</sup>|Evet|Evet|
|LINQ to SQL sınıfları|<sup>2</sup> yok|<sup>2</sup> yok|<sup>2</sup> yok|
|Hizmetler ( [!INCLUDE[ssAstoria](../includes/ssastoria-md.md)] WCF Hizmetleri ve Web Hizmetleri dahil)|Evet|Evet|Evet|
|Nesne|Evet|Evet|Evet|
|SharePoint|Evet|Evet|Evet|

 1. **Varlık veri modeli** Sihirbazı 'nı kullanarak modeli oluşturun ve ardından bu nesneleri tasarımcıya sürükleyin.

 2. LINQ to SQL sınıfları **veri kaynakları** penceresinde görünmez. Ancak, LINQ to SQL sınıfları temel alan yeni bir nesne veri kaynağı ekleyebilirsiniz ve ardından bu nesneleri tasarımcıya sürükleyerek veriye bağlı denetimler oluşturabilirsiniz. Daha fazla bilgi için bkz. [Izlenecek yol: LINQ to SQL sınıfları oluşturma (O-R Designer)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233).

## <a name="data-sources-window"></a>Veri Kaynakları penceresi
 Veri kaynakları, projenizde **veri kaynakları** penceresinde öğeler olarak kullanılabilir. Bu pencere görünür veya **Görünüm** menüsünden, form tasarım yüzeyi projenizdeki etkin pencere olduğunda erişilebilir. Bu penceredeki öğeleri, temel alınan verilere bağlanan denetimler oluşturmak için sürükleyebilir ve sağ tıklayarak da veri kaynaklarını yapılandırabilirsiniz.

 ![Veri Kaynakları penceresi](../data-tools/media/raddata-data-sources-window.png "radveri veri kaynakları penceresi")

 **Veri kaynakları** penceresinde görüntülenen her veri türü için, öğeyi tasarımcıya sürüklediğinizde varsayılan bir denetim oluşturulur. Bir öğeyi **veri kaynakları** penceresinden sürüklemeden önce, oluşturulacak denetimi değiştirebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresinden sürüklerken oluşturulacak denetimi ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md).

## <a name="tasks-involved-in-binding-controls-to-data"></a>Denetimlere veri bağlama ile ilgili görevler
 Aşağıdaki tabloda, denetimleri verilere bağlamak için gerçekleştirdiğiniz en yaygın görevlerden bazıları listelenmektedir.

|Görev|Daha fazla bilgi|
|----------|----------------------|
|**Veri kaynakları** penceresini açın.|Düzenleyicide bir tasarım yüzeyi açın ve **View**  >  **veri kaynaklarını**görüntüle ' yi seçin.|
|Projenize bir veri kaynağı ekleyin.|[Yeni veri kaynağı ekleme](../data-tools/add-new-data-sources.md)|
|**Veri kaynakları** penceresinden tasarımcıya bir öğe sürüklediğinizde oluşturulan denetimi ayarlayın.|[Veri Kaynakları penceresinden sürüklendiğinde denetimin oluşturulmasını ayarlama](../data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window.md)|
|**Veri kaynakları** penceresindeki öğelerle ilişkili denetimlerin listesini değiştirin.|[Veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md)|
|Veriye göre bağlantılı denetimler oluşturun.|[Visual Studio'da verilere Windows Forms denetimleri bağlama](../data-tools/bind-windows-forms-controls-to-data-in-visual-studio.md)<br /><br /> [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)|
|Bir nesne veya koleksiyona bağlayın.|[Visual Studio'da nesne bağlama](../data-tools/bind-objects-in-visual-studio.md)|
|Kullanıcı arabiriminde görünen verileri filtreleyin.|[Bir Windows Forms uygulamasındaki verileri filtreleme ve sıralama](../data-tools/filter-and-sort-data-in-a-windows-forms-application.md)|
|Denetimler için açıklamalı alt yazıları özelleştirin.|[Visual Studio'nun verilere bağlı denetimler için başlık oluşturma biçimini özelleştirme](../data-tools/customize-how-visual-studio-creates-captions-for-data-bound-controls.md)|

## <a name="see-also"></a>Ayrıca Bkz.
 .NET [Windows Forms veri bağlama](https://msdn.microsoft.com/library/c3826d8e-ea25-4ad4-a669-45bfb19192aa) [için Visual Studio veri araçları](../data-tools/visual-studio-data-tools-for-dotnet.md)

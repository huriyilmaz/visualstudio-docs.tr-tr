---
title: SharePoint Project sistemini genişletme | Microsoft Docs
description: SharePoint proje sistemini genişletin. SharePoint proje sistemini genişletmeyi öğrenin. Yaygın geliştirme görevlerini anlayın.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SharePoint development in Visual Studio, extending projects
- SharePoint development in Visual Studio, extending project items
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 0fea459c7a442d25363c66efc7be69d21a5e3fb2fd5b31b94e8f09665415d872
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121425394"
---
# <a name="extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
  Visual Studio bir dizi proje şablonu ve öğe şablonu kullanarak SharePoint çözüm oluşturabilirsiniz. Bu şablonlar birçok geliştirme senaryosunun gereksinimlerini karşılar, ancak ihtiyacınız olan işlevleri sağlamayan bazı durumları keşfedebilirsiniz. bu durumlarda, SharePoint proje sistemini genişletebilirsiniz.

## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint proje sistemine genel bakış
 SharePoint proje sistemi, *SharePoint proje öğelerinin* temel bileşenini temel alır. SharePoint proje öğesi, liste tanımı, Web bölümü veya içerik türü gibi tek bir SharePoint özelleştirmesini temsil eder.

 SharePoint projesi bir veya daha fazla SharePoint proje öğesi içeren bir Visual Studio projem. SharePoint projeler, proje öğelerinin dağıtım için özellikler ve paketler halinde nasıl gruplandığını tanımlayan ek bileşenler de içerir.

 SharePoint proje öğelerinin ve SharePoint projelerinin içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
 SharePoint proje sistemini aşağıdaki yollarla genişletebilirsiniz:

- kendi SharePoint proje öğesi türlerinizi tanımlayın ve bunları Visual Studio yeni öğe şablonlarıyla veya proje şablonlarıyla ilişkilendirin. örneğin, bir özel eylem veya bir alan oluşturmak için SharePoint proje öğesi türü tanımlayabilirsiniz. daha fazla bilgi için bkz. [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Visual Studio önceden yüklenmiş SharePoint proje öğesi türlerini genişletin. Örneğin, **Çözüm Gezgini** bir proje öğesine kısayol menü öğesi ekleyebilir ve bir geliştirici menü öğesini seçtiğinde Proje öğesini özelleştirebilirsiniz. daha fazla bilgi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).

- SharePoint projelerini genişletin. örneğin, SharePoint projelerine öğe eklendiğinde veya kaldırıldığında belirli görevleri gerçekleştirmek için olay işleyicileri ekleyebilirsiniz. daha fazla bilgi için bkz. [SharePoint projelerini genişletme](../sharepoint/extending-sharepoint-projects.md).

- SharePoint proje öğelerinin paketleme ve dağıtım davranışını ve SharePoint projelerini genişletin. örneğin, bir projeyi dağıtırken veya geri aldığınızda yürütmek üzere kendi dağıtım adımlarınızı oluşturabilir veya Visual Studio belirli dağıtım adımlarını yürüttüğünde ek özel görevler gerçekleştirebilirsiniz. daha fazla bilgi için bkz. [genişletme SharePoint paketleme ve dağıtım](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Ortak geliştirme görevleri
 SharePoint proje sisteminin uzantılarında aşağıdaki ortak görevleri gerçekleştirebilirsiniz:

- Özel dize verilerini proje öğeleriyle ve birçok farklı proje dosyası türünde kaydedin. daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- SharePoint proje sistemindeki bir nesneyi Visual Studio otomasyon nesne modeli veya tümleştirme nesne modelinde karşılık gelen bir nesneye dönüştürün veya bunun tersini yapın. daha fazla bilgi için [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında conver](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)' i inceleyin.

## <a name="see-also"></a>Ayrıca bkz.
- [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğelerini genişlet](../sharepoint/extending-sharepoint-project-items.md)
- [SharePoint projelerini genişlet](../sharepoint/extending-sharepoint-projects.md)
- [paketleme ve dağıtım SharePoint uzat](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [Visual Studio SharePoint araçlarını genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint Araç Uzantıları için Programlama Kavramları ve Özellikler](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)

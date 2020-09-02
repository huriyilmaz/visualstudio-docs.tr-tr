---
title: SharePoint proje sistemini genişletme | Microsoft Docs
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
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dce10c2bc44eb4fde6a6e38417d136ea5e9ba41
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62557030"
---
# <a name="extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
  Visual Studio 'da bir dizi proje şablonu ve öğe şablonu kullanarak SharePoint çözümleri oluşturabilirsiniz. Bu şablonlar birçok geliştirme senaryosunun gereksinimlerini karşılar, ancak ihtiyacınız olan işlevleri sağlamayan bazı durumları keşfedebilirsiniz. Bu gibi durumlarda, SharePoint proje sistemini genişletebilirsiniz.

## <a name="overview-of-the-sharepoint-project-system"></a>SharePoint proje sistemine genel bakış
 SharePoint proje sistemi, *SharePoint proje öğelerinin*temel bileşenini temel alır. SharePoint proje öğesi, liste tanımı, Web Bölümü veya içerik türü gibi tek bir SharePoint özelleştirmesini temsil eder.

 SharePoint projesi bir veya daha fazla SharePoint proje öğesi içeren bir Visual Studio projem. SharePoint projeleri ayrıca, proje öğelerinin dağıtım için özellikler ve paketler halinde nasıl gruplandığını tanımlayan ek bileşenler içerir.

 SharePoint proje öğelerinin ve SharePoint projelerinin içerikleri hakkında daha fazla bilgi için bkz. [SharePoint proje öğeleri için öğe şablonları ve proje şablonları oluşturma](../sharepoint/creating-item-templates-and-project-templates-for-sharepoint-project-items.md).

## <a name="how-to-extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
 SharePoint proje sistemini aşağıdaki yollarla genişletebilirsiniz:

- Kendi SharePoint proje öğe türlerinizi tanımlayın ve bunları Visual Studio 'da yeni öğe şablonlarıyla veya proje şablonlarıyla ilişkilendirin. Örneğin, özel bir eylem veya bir alan oluşturmak için bir SharePoint proje öğesi türü tanımlayabilirsiniz. Daha fazla bilgi için bkz. [özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md).

- Visual Studio 'da zaten yüklü olan SharePoint proje öğesi türlerini genişletin. Örneğin, **Çözüm Gezgini** bir proje öğesine kısayol menü öğesi ekleyebilir ve bir geliştirici menü öğesini seçtiğinde Proje öğesini özelleştirebilirsiniz. Daha fazla bilgi için bkz. [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md).

- SharePoint projelerini genişletin. Örneğin, SharePoint projelerine öğeler eklendiğinde veya kaldırıldığında belirli görevleri gerçekleştirmek için olay işleyicileri ekleyebilirsiniz. Daha fazla bilgi için bkz. [SharePoint projelerini genişletme](../sharepoint/extending-sharepoint-projects.md).

- SharePoint proje öğeleri ve SharePoint projelerinin paketleme ve dağıtım davranışını genişletin. Örneğin, bir projeyi dağıtırken veya geri aldığınızda yürütmek üzere kendi dağıtım adımlarınızı oluşturabilir veya Visual Studio belirli dağıtım adımlarını yürüttüğünde ek özel görevler gerçekleştirebilirsiniz. Daha fazla bilgi için bkz. [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md).

## <a name="common-development-tasks"></a>Ortak geliştirme görevleri
 SharePoint proje sisteminin uzantılarında aşağıdaki ortak görevleri gerçekleştirebilirsiniz:

- Özel dize verilerini proje öğeleriyle ve birçok farklı proje dosyası türünde kaydedin. Daha fazla bilgi için bkz. [SharePoint proje sisteminin uzantılarında verileri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md).

- SharePoint proje sistemindeki bir nesneyi Visual Studio Otomasyon nesne modeli veya Tümleştirme nesne modelinde karşılık gelen bir nesneye dönüştürün veya bunun tersini yapın. Daha fazla bilgi için bkz. [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında Conver](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md).

## <a name="see-also"></a>Ayrıca bkz.
- [Özel SharePoint proje öğesi türlerini tanımlama](../sharepoint/defining-custom-sharepoint-project-item-types.md)
- [SharePoint proje öğelerini genişletme](../sharepoint/extending-sharepoint-project-items.md)
- [SharePoint projelerini genişletme](../sharepoint/extending-sharepoint-projects.md)
- [SharePoint paketleme ve dağıtımını genişletme](../sharepoint/extending-sharepoint-packaging-and-deployment.md)
- [SharePoint proje sisteminin uzantılarında veri kaydetme](../sharepoint/saving-data-in-extensions-of-the-sharepoint-project-system.md)
- [SharePoint proje sistem türleri ve diğer Visual Studio proje türleri arasında dönüştürme](../sharepoint/converting-between-sharepoint-project-system-types-and-other-visual-studio-project-types.md)
- [SharePoint araçlarını Visual Studio 'da genişletme](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)
- [SharePoint Araç Uzantıları için Programlama Kavramları ve Özellikler](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)

---
title: SharePoint araçlarını Visual Studio 'da genişletme | Microsoft Docs
ms.date: 02/02/2017
ms.topic: overview
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- Visual Studio, extending tools
- extensibility [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, extending tools
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: 7dc0cc0d0af73d032d870629877b62c94e6b347b
ms.sourcegitcommit: f9e44f5ab6a1dfb56c945c9986730465e1adb6fc
ms.contentlocale: tr-TR
ms.lasthandoff: 07/06/2020
ms.locfileid: "86016039"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>SharePoint araçlarını Visual Studio 'da genişletme
  Visual Studio 'daki SharePoint araçları birçok uygulama geliştirme senaryosunun gereksinimlerini karşılar. Ancak, sizin veya diğer geliştiricilerin gerek duyduğu işlevleri sağlamayan durumlar bulabilirsiniz. Bu durumlarda, ihtiyacınız olan işlevleri oluşturmak için SharePoint araçlarını genişletebilirsiniz.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint araçlarını genişletme
 SharePoint proje sistemini ve **SharePoint bağlantıları** düğümünü **Sunucu Gezgini** penceresinde genişletebilirsiniz.

### <a name="extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
 Visual Studio, SharePoint çözümleri oluşturmak için kullanabileceğiniz bir proje şablonları ve öğe şablonları kümesi içerir. Örneğin, olay alıcıları, liste tanımları, iş akışları ve Web Bölümleri Şablonlar vardır. Ancak, alanlar veya özel eylemler gibi SharePoint bileşenleri oluşturmak için kendi SharePoint proje öğeleri türlerinizi de tanımlayabilirsiniz. Ayrıca, Visual Studio 'da zaten yüklü olan SharePoint proje öğesi türleri için uzantılar oluşturabilir ve SharePoint projeleri için Uzantılar oluşturabilirsiniz.

 Daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme
 Visual Studio 'da, hiyerarşik ağaç görünümünde bir veya daha fazla yerel SharePoint sitesinin bileşenlerinden birçoğunu görüntülemek için **Sunucu Gezgini** penceresindeki **SharePoint bağlantıları** düğümünü kullanabilirsiniz. **SharePoint bağlantıları** düğümünü aşağıdaki yollarla da genişletebilirsiniz:

- Kendi düğümlerinizi ekleyerek. Bu, varsayılan olarak görüntülenmeyen SharePoint sitelerinin bileşenlerini göstermek istiyorsanız yararlıdır.

- Mevcut düğümleri genişleterek. Örneğin, varolan bir düğüme yeni bir alt düğüm ekleyebilir veya bir geliştirici menü öğesini tıklattığında bir düğüme kısayol menü öğesi ekleyebilir ve görevleri gerçekleştirebilirsiniz.

  Daha fazla bilgi için, bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Geliştirme bilgisayarı gereksinimleri
 SharePoint araçları için uzantı oluşturmak üzere geliştirme bilgisayarınızın, Visual Studio 'da SharePoint çözümleri oluşturmak için aynı gereksinimleri karşılaması gerekir.

 Ayrıca, yüklemenizi öneririz [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . SDK, Visual Studio 'Yu genişletmek için kullanabileceğiniz proje şablonlarını ve araçları içerir. Özellikle, SDK, Visual Studio uzantısı (VSıX) paketini kolayca oluşturmak için kullanabileceğiniz bir proje şablonu içerir. VSıX paketleri Visual Studio 'da Visual Studio uzantıları dağıtmanın tercih edilen yoludur. Tüm SharePoint araçları uzantılarının VSıX paketleri kullanılarak dağıtılması gerekir. Bu belgelerdeki tüm izlenecek yollar, yüklü olduğunu varsayar [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] .

 Visual Studio SDK 'yı yüklemek için bkz. [Visual STUDIO SDK 'Yı yükleme](../extensibility/installing-the-visual-studio-sdk.md). Visual Studio uzantıları hakkında daha fazla bilgi için bkz. [Visual Studio uzantıları geliştirmeye başlama](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint Araç uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint Araçları uzantıları için programlama kavramları ve özellikleri](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [SharePoint Araçları Genişletilebilirliği &#40;başvuru&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio 'da SharePoint araçları için hata ayıklama uzantıları](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio 'da SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
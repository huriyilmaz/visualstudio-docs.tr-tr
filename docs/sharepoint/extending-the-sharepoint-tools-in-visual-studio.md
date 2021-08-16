---
title: Visual Studio SharePoint araçlarını genişletme | Microsoft Docs
description: SharePoint araçlarını Visual Studio genişletin. SharePoint proje sistemini genişletin. Sunucu Gezgini SharePoint bağlantıları düğümünü genişletin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: 2f58bc342eb4066bff744912bbdcd154c9dc580ecacb17f5f1117acc91a1cb62
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121409650"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>Visual Studio SharePoint araçlarını genişletme
  Visual Studio ' deki SharePoint araçları birçok uygulama geliştirme senaryosunun gereksinimlerini karşılar. Ancak, sizin veya diğer geliştiricilerin gerek duyduğu işlevleri sağlamayan durumlar bulabilirsiniz. bu durumlarda, ihtiyacınız olan işlevleri oluşturmak için SharePoint araçlarını genişletebilirsiniz.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint araçlarını genişletme
 SharePoint proje sistemini ve **SharePoint bağlantıları** düğümünü **Sunucu Gezgini** penceresinde genişletebilirsiniz.

### <a name="extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
 Visual Studio, SharePoint çözümleri oluşturmak için kullanabileceğiniz bir proje şablonları ve öğe şablonları kümesi içerir. örneğin, olay alıcıları, liste tanımları, iş akışları ve Web Bölümleri şablonlar vardır. ancak, alanlar veya özel eylemler gibi SharePoint bileşenleri oluşturmak için kendi SharePoint proje öğesi türlerinizi de tanımlayabilirsiniz. ayrıca, Visual Studio zaten yüklenmiş SharePoint proje öğesi türleri için uzantılar oluşturabilir ve SharePoint projeleri için uzantılar oluşturabilirsiniz.

 daha fazla bilgi için bkz. [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md).

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme
 Visual Studio ' de, bir veya daha fazla yerel SharePoint sitesinin birçok bileşenini hiyerarşik bir ağaç görünümünde görüntülemek için **Sunucu Gezgini** penceresindeki **SharePoint bağlantılar** düğümünü kullanabilirsiniz. **SharePoint Connections** düğümünü aşağıdaki yollarla da genişletebilirsiniz:

- Kendi düğümlerinizi ekleyerek. bu, varsayılan olarak görüntülenmeyen SharePoint sitelerin bileşenlerini göstermek istiyorsanız yararlıdır.

- Mevcut düğümleri genişleterek. Örneğin, varolan bir düğüme yeni bir alt düğüm ekleyebilir veya bir geliştirici menü öğesini tıklattığında bir düğüme kısayol menü öğesi ekleyebilir ve görevleri gerçekleştirebilirsiniz.

  daha fazla bilgi için bkz. [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md).

## <a name="development-computer-requirements"></a>Geliştirme bilgisayarı gereksinimleri
 SharePoint araçları için uzantı oluşturmak üzere geliştirme bilgisayarınızın, Visual Studio SharePoint çözümleri oluşturmak için aynı gereksinimleri karşılaması gerekir.

 Ayrıca, yüklemenizi öneririz [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] . SDK, Visual Studio genişletmek için kullanabileceğiniz proje şablonlarını ve araçları içerir. özellikle, SDK Visual Studio uzantısı (vsıx) paketini kolayca oluşturmak için kullanabileceğiniz bir proje şablonu içerir. vsıx paketleri Visual Studio Visual Studio uzantıları dağıtmak için tercih edilen yoldur. tüm SharePoint araçları uzantılarının vsıx paketleri kullanılarak dağıtılması gerekir. Bu belgelerdeki tüm izlenecek yollar, yüklü olduğunu varsayar [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] .

 Visual Studio sdk 'yı yüklemek için, bkz. [Visual Studio sdk 'yı yükleme](../extensibility/installing-the-visual-studio-sdk.md). Visual Studio uzantıları hakkında daha fazla bilgi için bkz. [Visual Studio uzantıları geliştirmeye başlama](../extensibility/starting-to-develop-visual-studio-extensions.md).

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [SharePoint proje sistemini genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Sunucu Gezgini SharePoint bağlantıları düğümünü genişletme](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint araçları uzantıları için programlama kavramları ve özellikleri](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [başvuru &#40;SharePoint araçları genişletilebilirliği&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio SharePoint araçları için hata ayıklama uzantıları](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio SharePoint araçları için uzantıları dağıtma](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
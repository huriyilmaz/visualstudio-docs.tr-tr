---
title: Visual Studio |'SharePoint Araçları'nın Visual Studio | Microsoft Docs
description: SharePoint'daki Visual Studio. Yeni proje SharePoint genişletme. Kümedeki SharePoint düğümünü Sunucu Gezgini.
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
ms.openlocfilehash: 31165f4d3f9b70fe9848163c8a3771cc8e886e1f
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625257"
---
# <a name="extend-the-sharepoint-tools-in-visual-studio"></a>SharePoint'daki SharePoint araçları Visual Studio
  SharePoint geliştirme Visual Studio birçok uygulama geliştirme senaryosunun gereksinimlerini karşılamaya yardımcı olur. Ancak, sizin veya diğer geliştiricilerin ihtiyaçlarında işlev sağlamama durumlarını keşfedersiniz. Böyle durumlarda, ihtiyaç SharePoint oluşturmak için uygulama araçlarını genişletebilirsiniz.

## <a name="how-to-extend-the-sharepoint-tools"></a>SharePoint araçları genişletme
 Sunucu Gezgini penceresinde SharePoint proje sistemini ve **SharePoint** Bağlantılar **düğümünü genişletebilirsiniz.**

### <a name="extend-the-sharepoint-project-system"></a>SharePoint proje sistemini genişletme
 Visual Studio çözüm oluşturmak için kullanabileceğiniz bir dizi proje şablonu ve öğe SharePoint içerir. Örneğin, olay alıcıları, liste tanımları, iş akışları ve iş akışları için şablonlar Web Bölümleri. Bununla birlikte, alanlar veya özel eylemler gibi SharePoint bileşenleri oluşturmak için SharePoint proje öğelerinizi de tanımlayabilirsiniz. Ayrıca, Visual Studio'SharePoint proje öğesi türleri için uzantılar oluşturabilir ve SharePoint için uzantılar oluşturabilirsiniz.

 Daha fazla bilgi için [bkz. SharePoint proje sistemini genişletme.](../sharepoint/extending-the-sharepoint-project-system.md)

### <a name="extend-the-sharepoint-connections-node-in-server-explorer"></a>Kümedeki SharePoint düğümünü Sunucu Gezgini
 Bu Visual Studio, **Sunucu Gezgini** penceresindeki **SharePoint** Bağlantıları düğümünü kullanarak bir veya daha fazla yerel SharePoint sitenin bileşenlerini hiyerarşik ağaç görünümünde görüntüebilirsiniz. Ağ Bağlantıları **düğümünü SharePoint aşağıdaki** yollarla genişletebilirsiniz:

- Kendi düğümlerinizi ekleyerek. Bu, varsayılan olarak görüntülenmez sitelerinin SharePoint görüntülemek için kullanışlıdır.

- Mevcut düğümleri genişleterek. Örneğin, mevcut bir düğüme yeni bir alt düğüm ekleyebilir veya bir düğüme kısayol menü öğesi ekleyebilir ve geliştirici menü öğesini tıkladığında görevler gerçekleştirebilirsiniz.

  Daha fazla bilgi için [bkz. SharePoint'de bağlantı düğümünü Sunucu Gezgini.](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)

## <a name="development-computer-requirements"></a>Geliştirme bilgisayarı gereksinimleri
 Geliştirme araçlarına yönelik uzantılar SharePoint için, geliştirme bilgisayarınızın bu araçlarda yeni çözüm oluşturmak SharePoint gereksinimleri Visual Studio.

 ayrıca yüklemenizi [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] öneririz. SDK, proje şablonlarını ve bu şablonları genişletmek için kullanabileceğiniz Visual Studio. Sdk özellikle bir Visual Studio Uzantısı (VSIX) paketi oluşturmak için kullanabileceğiniz bir proje şablonu içerir. VSIX paketleri, sanal ağlarda Visual Studio için tercih edilen Visual Studio. Tüm SharePoint araçları uzantıları VSIX paketleri kullanılarak dağıtılabilir. Bu belgelerde yer alan tüm kılavuzlarda yüklü olduğu [!INCLUDE[vssdk_current_long](../sharepoint/includes/vssdk-current-long-md.md)] varsayıldı.

 Visual Studio SDK'yı yüklemek için [bkz. Visual Studio SDK'sı yükleme.](../extensibility/installing-the-visual-studio-sdk.md) Uzantılar hakkında daha fazla Visual Studio için bkz. Yeni [Uzantılar Visual Studio Başlama.](../extensibility/starting-to-develop-visual-studio-extensions.md)

## <a name="see-also"></a>Ayrıca bkz.

- [SharePoint araçları uzantılarının programlama modeline genel bakış](../sharepoint/overview-of-the-programming-model-of-sharepoint-tools-extensions.md)
- [Proje SharePoint genişletme](../sharepoint/extending-the-sharepoint-project-system.md)
- [Kümedeki SharePoint düğümünü Sunucu Gezgini](../sharepoint/extending-the-sharepoint-connections-node-in-server-explorer.md)
- [SharePoint araçları uzantıları için programlama kavramları ve özellikleri](../sharepoint/programming-concepts-and-features-for-sharepoint-tools-extensions.md)
- [Başvuru &#40;SharePoint Araçları genişletilebilirlik&#41;](../sharepoint/reference-sharepoint-tools-extensibility.md)
- [Visual Studio'de SharePoint için uzantılarda hata Visual Studio](../sharepoint/debugging-extensions-for-the-sharepoint-tools-in-visual-studio.md)
- [Visual Studio'de SharePoint araçları için uzantıları Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)
---
title: 'Nasıl yapılır: şablonlarda sorun giderme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: troubleshooting
helpviewer_keywords:
- Visual Studio templates, troubleshooting
ms.assetid: 3e577ad2-f725-4c11-93b3-477f2404ec81
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: c481b2b9c90b15f4cbc709cad89e5b772ad95cee
ms.sourcegitcommit: 374f5ec9a5fa18a6d4533fa2b797aa211f186755
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/20/2020
ms.locfileid: "77477091"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl Yapılır: Şablonlarda Sorun Giderme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Geliştirme ortamında yüklemek bir şablon başarısız olursa, sorunu bulmak için birkaç yolu vardır.

## <a name="validating-the-vstemplate-file"></a>. Vstemplate dosyasını doğrulama
 Bir şablondaki. vstemplate dosyası [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablon şemasına bağlı değilse, şablon **Yeni proje** iletişim kutusunda görünmeyebilir.

#### <a name="to-validate-the-vstemplate-file"></a>. Vstemplate dosyasını doğrulamak için

1. Şablonu içeren. zip dosyasını bulun.

2. . Zip dosyasını ayıklayın.

3. [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**Dosya** menüsünde **Aç**' a ve ardından **Dosya**' ya tıklayın.

4. Şablon için. vstemplate dosyasını seçin ve **Aç**' a tıklayın.

5. . Vstemplate dosyasının XML dosyasının [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] şablon şemasına bağlı olduğunu doğrulayın. . Vstemplate şeması hakkında daha fazla bilgi için bkz. [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > . Vstemplate dosyasını yazarken IntelliSense desteği almak için, `VSTemplate` öğesine bir `xmlns` özniteliği ekleyin ve bu değere `http://schemas.microsoft.com/developer/vstemplate/2005`değerini atayın.

6. . Vstemplate dosyasını kaydedin ve kapatın.

7. Şablonunuza dahil olan dosyaları seçin, sağ tıklayın, Gönder ' i seçin ve **Sıkıştırılmış (daraltılmış) klasör**' **e**tıklayın. Seçtiğiniz dosyalar bir. zip dosyasında sıkıştırılır.

8. Yeni. zip dosyasını eski. zip dosyası ile aynı dizine yerleştirin.

9. Ayıklanan şablon dosyalarını ve eski şablon. zip dosyasını silin.

## <a name="monitoring-the-event-log"></a>Olay günlüğünü izleme
 şablon. zip dosyaları işlenirken [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] günlük hatalarıyla karşılaşıldı. Şablon **Yeni proje** iletişim kutusunda beklendiği gibi görünmüyorsa, sorunu gidermek için **Olay Görüntüleyicisi** kullanabilirsiniz.

#### <a name="to-locate-template-errors-in-event-viewer"></a>Olay Görüntüleyicisi şablon hatalarını bulmak için

1. Windows 'da **Başlat**' a tıklayın, **Denetim Masası**' na tıklayın, **Yönetimsel Araçlar**' a çift tıklayın ve ardından **Olay Görüntüleyicisi**' ye çift tıklayın.

2. Sol bölmede **uygulama**' ya tıklayın.

3. **Kaynak** değeri `Visual Studio - VsTemplate`olan olayları arayın.

4. Hatayı görüntülemek için bir şablon olayına çift tıklayın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md) [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md) [Visual Studio Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)

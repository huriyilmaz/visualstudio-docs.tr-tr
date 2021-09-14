---
title: Proje şablonları ve öğe şablonlarının sorunlarını giderme
description: Geliştirme ortamında yük devredediklerinde şablonların sorunlarını nasıl giderebileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.openlocfilehash: 00580c7a1e63dd3c68fc9a86b67812ed3a1dfa8b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725753"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl yapılır: şablonlarda sorun giderme

Bir şablon geliştirme ortamında yüklenemezse, sorunu bulmanın birkaç yolu vardır.

## <a name="validate-the-vstemplate-file"></a>Vstemplate dosyasını doğrulama

::: moniker range="vs-2017"

bir şablondaki *vstemplate* dosyası Visual Studio şablon şemasına bağlı değilse, şablon **yeni Project** iletişim kutusunda görünmeyebilir.

::: moniker-end

::: moniker range=">=vs-2019"

bir şablondaki *vstemplate* dosyası Visual Studio şablon şemasına bağlı değilse, şablon yeni projeler oluşturduğunuz iletişim kutusunda görünmeyebilir.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Vstemplate dosyasını doğrulamak için

1. Şablonu içeren *.zip* dosyasını bulun.

1. *.zip* dosyasını ayıklayın.

1. Visual Studio **dosya** menüsünde dosya aç ' ı seçin   >  .

1. Şablon için *vstemplate* dosyasını seçin ve **Aç**' ı seçin.

1. *Vstemplate* dosyasının XML dosyasının şablon şemasına bağlı olduğunu doğrulayın. *Vstemplate* şeması hakkında daha fazla bilgi için bkz. [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > *Vstemplate* dosyasını yazarken IntelliSense desteği almak için, öğesine bir öznitelik ekleyin `xmlns` `VSTemplate` ve değeri atayın `http://schemas.microsoft.com/developer/vstemplate/2005` .

1. *Vstemplate* dosyasını kaydedin ve kapatın.

1. Şablonunuza dahil olan dosyaları seçin, sağ tıklayın ve   >  **Sıkıştırılmış (daraltılmış) klasöre** Gönder ' i seçin. Seçtiğiniz dosyalar bir *.zip* dosyasında sıkıştırılır.

1. Yeni *.zip* dosyasını eski *.zip* dosyası ile aynı dizine yerleştirin.

1. Ayıklanan şablon dosyalarını ve eski şablon *.zip* dosyasını silin.

## <a name="enable-diagnostic-logging"></a>Tanılama günlüğünü etkinleştirme

Şablon [bulma sorunlarını giderme (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md)bölümündeki adımları izleyerek şablon bulma için tanılama günlüğünü etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma sorunlarını giderme (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)

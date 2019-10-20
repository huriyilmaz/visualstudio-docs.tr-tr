---
title: Proje şablonu ve öğe şablonu yükleme sorunlarını giderme
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0dbdb2854833f7c28866aa3d6ec0a685803adb3d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656546"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl yapılır: şablonlarda sorun giderme

Bir şablon geliştirme ortamında yüklenemezse, sorunu bulmanın birkaç yolu vardır.

## <a name="validate-the-vstemplate-file"></a>Vstemplate dosyasını doğrulama

::: moniker range="vs-2017"

Şablondaki *vstemplate* dosyası Visual Studio şablon şemasına bağlı değilse, şablon **Yeni proje** iletişim kutusunda görünmeyebilir.

::: moniker-end

::: moniker range=">=vs-2019"

Bir şablondaki *vstemplate* dosyası Visual Studio şablon şemasına bağlı değilse, şablon yeni projeler oluşturduğunuz iletişim kutusunda görünmeyebilir.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Vstemplate dosyasını doğrulamak için

1. Şablonu içeren *. zip* dosyasını bulun.

1. *. Zip* dosyasını ayıklayın.

1. Visual Studio 'daki **Dosya** menüsünde  > **dosyayı** **Aç** ' ı seçin.

1. Şablon için *vstemplate* dosyasını seçin ve **Aç**' ı seçin.

1. *Vstemplate* dosyasının XML dosyasının şablon şemasına bağlı olduğunu doğrulayın. *Vstemplate* şeması hakkında daha fazla bilgi için bkz. [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > *Vstemplate* dosyasını yazarken IntelliSense desteği almak için, `VSTemplate` öğesine bir `xmlns` özniteliği ekleyin ve bu değere http://schemas.microsoft.com/developer/vstemplate/2005 değerini atayın.

1. *Vstemplate* dosyasını kaydedin ve kapatın.

1. Şablonunuza dahil olan dosyaları seçin, sağ tıklayın ve  > **Sıkıştırılmış (daraltılmış) klasöre** **Gönder** ' i seçin. Seçtiğiniz dosyalar bir *. zip* dosyasında sıkıştırılır.

1. Yeni *. zip* dosyasını eski *. zip* dosyası ile aynı dizine yerleştirin.

1. Ayıklanan şablon dosyalarını ve eski şablon *. zip* dosyasını silin.

## <a name="enable-diagnostic-logging"></a>Tanılama günlüğünü etkinleştirme

Şablon [bulma sorunlarını giderme (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md)bölümündeki adımları izleyerek şablon bulma için tanılama günlüğünü etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma sorunlarını giderme (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)
---
title: Sorun giderme proje şablonu ve madde şablonu yükleme
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75591391"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl yapılı: Şablonları sorun giderme

Şablon geliştirme ortamında yüklenmezse, sorunu bulmanın birkaç yolu vardır.

## <a name="validate-the-vstemplate-file"></a>vstemplate dosyasını doğrulama

::: moniker range="vs-2017"

Şablondaki *vstemplate* dosyası Visual Studio şablon şemasına uymuyorsa, şablon **Yeni Proje** iletişim kutusunda görünmeyebilir.

::: moniker-end

::: moniker range=">=vs-2019"

Şablondaki *vstemplate* dosyası Visual Studio şablon şemasına uymuyorsa, şablon yeni projeler oluşturduğunuz iletişim kutusunda görünmeyebilir.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>vstemplate dosyasını doğrulamak için

1. Şablonu içeren *.zip* dosyasını bulun.

1. *.zip* dosyasını ayıklayın.

1. Visual Studio'daki **Dosya** menüsünde **Dosyaaç'ı** > **File**seçin.

1. Şablon için *vstemplate* dosyasını seçin ve **Aç'ı**seçin.

1. *Vstemplate* dosyasının XML'sinin şablon şemasına uydur luğunu doğrulayın. *vstemplate* şeması hakkında daha fazla bilgi için [bkz.](../extensibility/visual-studio-template-schema-reference.md)

    > [!NOTE]
    > *Vstemplate* dosyasını yazarken IntelliSense desteğini almak `xmlns` için, `VSTemplate` öğeye bir öznitelik ekleyin `http://schemas.microsoft.com/developer/vstemplate/2005`ve bir değer atayın.

1. *vstemplate* dosyasını kaydedin ve kapatın.

1. Şablonunuzda bulunan dosyaları seçin, sağ tıklayın ve > **Sıkıştırılmış (sıkıştırılmış) klasörüne Gönder'i**seçin. **Send to** Seçtiğiniz dosyalar *bir .zip* dosyasına sıkıştırılır.

1. Yeni *.zip* dosyasını eski *.zip* dosyasıyla aynı dizine yerleştirin.

1. Çıkarılan şablon dosyalarını ve eski şablon *.zip* dosyasını silin.

## <a name="enable-diagnostic-logging"></a>Tanılama günlüğünü etkinleştirme

[Sorun giderme şablonu bulma (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md)adımlarını izleyerek şablon bulma için tanılama günlüğe kaydetmeyi etkinleştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Sorun giderme şablonu bulma (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon şema başvurusu](../extensibility/visual-studio-template-schema-reference.md)

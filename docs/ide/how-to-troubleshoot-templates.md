---
title: Proje şablonu ve öğe şablonu yüklenirken sorun giderme
ms.date: 01/02/2018
ms.topic: troubleshooting
helpviewer_keywords:
- templates [Visual Studio], troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: 1bef6a460f1a59823930597565b955b591ab48a0
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75591391"
---
# <a name="how-to-troubleshoot-templates"></a>Nasıl yapılır: şablonlarda sorun giderme

Geliştirme ortamında yüklemek bir şablon başarısız olursa, sorunu bulmak için birkaç yolu vardır.

## <a name="validate-the-vstemplate-file"></a>Vstemplate dosyası doğrula

::: moniker range="vs-2017"

Varsa *vstemplate* şablon dosyasında için Visual Studio şablon şeması uyması değil, şablon görüntülenmeyebilir **yeni proje** iletişim kutusu.

::: moniker-end

::: moniker range=">=vs-2019"

Bir şablondaki *vstemplate* dosyası Visual Studio şablon şemasına bağlı değilse, şablon yeni projeler oluşturduğunuz iletişim kutusunda görünmeyebilir.

::: moniker-end

### <a name="to-validate-the-vstemplate-file"></a>Vstemplate dosyası doğrulamak için

1. Bulun *.zip* şablonu içeren dosya.

1. Ayıklama *.zip* dosya.

1. Üzerinde **dosya** Visual Studio menüsünde **açık** > **dosya**.

1. Seçin *vstemplate* dosya şablonu ve seçin **açık**.

1. Doğrulayın, XML *vstemplate* dosyası için şablon şeması uyar. Daha fazla bilgi için *vstemplate* şema bakın [şablon şeması başvurusu](../extensibility/visual-studio-template-schema-reference.md).

    > [!NOTE]
    > Geliştirme sırasında IntelliSense desteği almak için *vstemplate* ekleyin bir `xmlns` özniteliğini `VSTemplate` öğesini ve değerini atayın `http://schemas.microsoft.com/developer/vstemplate/2005`.

1. Kaydet ve Kapat *vstemplate* dosya.

1. Şablonunuzda, içerdiği dosyaları seçin, sağ tıklatın ve seçin **göndermek** > **sıkıştırılmış (daraltılmış) klasör**. Seçtiğiniz dosyalar sıkıştırılmadan bir *.zip* dosya.

1. Yeni yerleştirin *.zip* eski ile aynı dizinde dosya *.zip* dosya.

1. Ayıklanan şablon dosyalarını ve eski şablonu silmek *.zip* dosya.

## <a name="enable-diagnostic-logging"></a>Tanılama günlüğünü etkinleştirme

İçindeki adımları izleyerek, şablon keşfi için tanılama günlük kaydını etkinleştirebilirsiniz [sorun giderme şablon bulma (genişletilebilirlik)](../extensibility/troubleshooting-template-discovery.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Şablon bulma (genişletilebilirlik) sorunlarını giderme](../extensibility/troubleshooting-template-discovery.md)
- [Şablonları özelleştirme](../ide/customizing-project-and-item-templates.md)
- [Proje ve öğe şablonları oluşturma](../ide/creating-project-and-item-templates.md)
- [Şablon Şeması Başvurusu](../extensibility/visual-studio-template-schema-reference.md)

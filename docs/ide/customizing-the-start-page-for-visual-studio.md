---
title: Başlangıç deneyimini değiştirme
ms.date: 02/01/2017
ms.topic: conceptual
f1_keywords:
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start Page
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 281a0c43c0163d158151683e9fdc483dfc1709f5
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75567222"
---
# <a name="customize-startup"></a>Başlatmayı özelleştir

Visual Studio için başlangıç deneyimini, en son çözümünüzü açmak veya boş bir geliştirme ortamı gibi birkaç farklı şekilde özelleştirebilirsiniz.

::: moniker range="vs-2017"

Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Başlangıç öğesini değiştirmek için

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

2. **Ortamı**Genişlet ve ardından **Başlangıç'ı**seçin.

::: moniker range="vs-2017"

3. **Başlangıç** listesinde Visual Studio başlattıktan sonra görüntülenecek öğeyi seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. Açık **başlangıç listesinde,** Visual Studio başlattıktan sonra ne olmasını istediğinizi seçin. **Başlat penceresinden** (yeni veya varolan bir proje açmanızı sağlayan), **en son çözüm**veya Boş **ortam**arasından seçim yapabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Özel bir başlangıç sayfası göstermek için

Visual Studio SDK'yı kullanarak [kendi özel başlangıç sayfanızı oluşturabilir](../extensibility/creating-a-custom-start-page.md) veya başka birinin zaten oluşturduğu bir sayfayı kullanabilirsiniz. Örneğin, [Visual Studio Marketplace'te](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads)özel başlangıç sayfaları bulabilirsiniz.

Özel bir başlangıç sayfası yüklemek için *.vsix* dosyasını açın veya başlangıç sayfası dosyalarını bilgisayarınızdaki *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* klasörüne kopyalayıp yapıştırın.

### <a name="to-select-which-custom-start-page-to-display"></a>Görüntülenecek özel başlangıç sayfasını seçmek için

1. Menü çubuğunda **Araç** > **Seçenekleri'ni**seçin.

1. **Ortamı**Genişlet ve ardından **Başlangıç'ı**seçin.

1. Başlangıç **Sayfasını Özelleştir** listesinde istediğiniz sayfayı seçin.

> [!TIP]
> Özel bir başlangıç sayfasındaki bir hata Visual Studio'nun çökmesine neden oluyorsa, Visual Studio'yu güvenli modda açabilir ve varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz. [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'yi kişiselleştirin](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end

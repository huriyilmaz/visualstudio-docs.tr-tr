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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75567222"
---
# <a name="customize-startup"></a>Başlangıç Özelleştir

Visual Studio için başlangıç deneyimini, en son çözümünüzü açma veya yalnızca boş bir geliştirme ortamı gibi birçok farklı yolla özelleştirebilirsiniz.

::: moniker range="vs-2017"

Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Başlangıç öğesini değiştirmek için

1. Menü çubuğunda, **Araçları** > **seçenekleri**.

2. Genişletin **ortam**ve ardından **başlangıç**.

::: moniker range="vs-2017"

3. İçinde **başlangıçta** listesinde, Visual Studio'yu başlattıktan sonra görüntülenecek öğeyi seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. **Başlangıçta,** listede, Visual Studio başlatıldıktan sonra ne olmasını istediğinizi seçin. **Başlangıç penceresi** (yeni veya var olan bir proje açmanıza olanak tanır), **en son çözüm**veya **boş ortam**arasından seçim yapabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Özel başlangıç sayfası göstermek için

Yapabilecekleriniz [kendi özel başlangıç sayfası oluşturma](../extensibility/creating-a-custom-start-page.md) Visual Studio SDK'sını kullanarak veya bir başkası zaten oluşturduğu kullanın. Örneğin, özel başlangıç sayfalarda bulabilirsiniz [Visual Studio Market](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads).

Özel başlangıç sayfası yüklemek için açın *.vsix* dosyası veya kopyalayın ve başlangıç sayfası dosyalarına yapıştırın *%USERPROFILE%\Documents\Visual Studio 2017\StartPages* bilgisayarınızda bir klasör.

### <a name="to-select-which-custom-start-page-to-display"></a>Görüntülenecek hangi özel başlangıç sayfası seçin

1. Menü çubuğunda **araçlar** > **Seçenekler**' i seçin.

1. Genişletin **ortam**ve ardından **başlangıç**.

1. İçinde **başlangıç sayfasını Özelleştir** listesinde, istediğiniz sayfayı seçin.

> [!TIP]
> Özel başlangıç sayfasındaki bir hata, Visual Studio 'Nun kilitlenmesine neden oluyorsa, Visual Studio 'Yu güvenli modda açıp varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz: [safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end

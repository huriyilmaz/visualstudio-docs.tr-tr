---
title: Başlangıç deneyimini değiştirme
description: sizin için en faydalı araçlarla Visual Studio açılacak şekilde, başlangıç deneyiminizi özelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 0814d4f7c9be48ef881d80d835a28c93921317e8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122109402"
---
# <a name="customize-startup"></a>Başlangıç Özelleştir

Visual Studio başlangıç deneyimini, en son çözümünüzü açma veya yalnızca boş bir geliştirme ortamı gibi birçok farklı şekilde özelleştirebilirsiniz.

::: moniker range="vs-2017"

Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Başlangıç öğesini değiştirmek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve ardından **Başlangıç**' ı seçin.

::: moniker range="vs-2017"

3. **At başlangıç** listesinde Visual Studio başlatıldıktan sonra görüntülenecek öğeyi seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. **başlangıçta,** listede, Visual Studio başlatıldıktan sonra ne olmasını istediğinizi seçin. **Başlangıç penceresi** (yeni veya var olan bir proje açmanıza olanak tanır), **en son çözüm** veya **boş ortam** arasından seçim yapabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Özel bir başlangıç sayfası göstermek için

Visual Studio SDK 'sını kullanarak [kendi özel başlangıç sayfanızı oluşturabilir](../extensibility/creating-a-custom-start-page.md) veya başka birisinin zaten oluşturduğu bir tane kullanabilirsiniz. örneğin, [Visual Studio marketi](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads)'nde özel başlangıç sayfaları bulabilirsiniz.

özel bir başlangıç sayfası yüklemek için *. vsix* dosyasını açın veya başlangıç sayfası dosyalarını kopyalayıp bilgisayarınızdaki *%userprofıle%\documents\ Visual Studio 2017 \ startpages* klasörüne yapıştırın.

### <a name="to-select-which-custom-start-page-to-display"></a>Görüntülenecek özel başlangıç sayfasını seçmek için

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. **Ortam**' ı genişletin ve ardından **Başlangıç**' ı seçin.

1. **Başlangıç sayfası Özelleştir** listesinde istediğiniz sayfayı seçin.

> [!TIP]
> özel başlangıç sayfasındaki bir hata kilitlenme Visual Studio neden oluyorsa, Visual Studio güvenli modda açabilir ve ardından varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz. [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio ıde 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end

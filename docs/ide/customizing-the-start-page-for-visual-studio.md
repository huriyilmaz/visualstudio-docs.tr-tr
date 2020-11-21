---
title: Başlangıç deneyimini değiştirme
description: Size en faydalı araçlarla Visual Studios açılacak şekilde, başlangıç deneyiminizi özelleştirmeyi öğrenin.
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 827ac67840f272e17cec6a7882a02b58dddbf925
ms.sourcegitcommit: 66cda27b63c9b55782b1db223a6dbda9f8cabe13
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/21/2020
ms.locfileid: "95006269"
---
# <a name="customize-startup"></a>Başlangıç Özelleştir

Visual Studio için başlangıç deneyimini, en son çözümünüzü açma veya yalnızca boş bir geliştirme ortamı gibi birçok farklı yolla özelleştirebilirsiniz.

::: moniker range="vs-2017"

Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Başlangıç öğesini değiştirmek için

1. Menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve ardından **Başlangıç**' ı seçin.

::: moniker range="vs-2017"

3. **At başlangıç** listesinde, Visual Studio başlatıldıktan sonra görüntülenecek öğeyi seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. **Başlangıçta,** listede, Visual Studio başlatıldıktan sonra ne olmasını istediğinizi seçin. **Başlangıç penceresi** (yeni veya var olan bir proje açmanıza olanak tanır), **en son çözüm** veya **boş ortam** arasından seçim yapabilirsiniz.

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Özel bir başlangıç sayfası göstermek için

Visual Studio SDK 'sını kullanarak [kendi özel başlangıç sayfanızı oluşturabilir](../extensibility/creating-a-custom-start-page.md) veya başka birisinin zaten oluşturduğu bir tane kullanabilirsiniz. Örneğin, [Visual Studio Market](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads)özel başlangıç sayfaları bulabilirsiniz.

Özel bir başlangıç sayfası yüklemek için *. vsix* dosyasını açın veya başlangıç sayfası dosyalarını kopyalayıp bilgisayarınızdaki *%userprofile%\Bir Studio 2017 \ startpages* klasörüne yapıştırın.

### <a name="to-select-which-custom-start-page-to-display"></a>Görüntülenecek özel başlangıç sayfasını seçmek için

1. Menü çubuğunda **Araçlar** > **Seçenekler**' i seçin.

1. **Ortam**' ı genişletin ve ardından **Başlangıç**' ı seçin.

1. **Başlangıç sayfası Özelleştir** listesinde istediğiniz sayfayı seçin.

> [!TIP]
> Özel başlangıç sayfasındaki bir hata, Visual Studio 'Nun kilitlenmesine neden oluyorsa, Visual Studio 'Yu güvenli modda açıp varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz. [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio IDE 'yi kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end

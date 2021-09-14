---
title: Başlangıç deneyimini değiştirme
description: Başlangıç deneyiminizi, sizin için en Visual Studio araçlarla açacak şekilde özelleştirmeyi öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126625958"
---
# <a name="customize-startup"></a>Başlatmayı özelleştirme

Başlangıç deneyimini en son Visual Studio veya yalnızca boş bir geliştirme ortamını açma gibi birkaç farklı şekilde özelleştirebilirsiniz.

::: moniker range="vs-2017"

Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

::: moniker-end

## <a name="to-change-the-startup-item"></a>Başlangıç öğesini değiştirmek için

1. Menü çubuğunda Araçlar **Seçenekleri'ne**  >  **tıklayın.**

2. **Ortam'ı** genişletin ve ardından Başlangıç'ı **seçin.**

::: moniker range="vs-2017"

3. Başlangıçta **listesinde,** başlatmadan sonra görüntülenecek öğeyi Visual Studio seçin.

::: moniker-end

::: moniker range=">=vs-2019"

3. Başlangıçta, **aç listesinde,** başlatmadan sonra ne olmasını Visual Studio seçin. Başlangıç penceresinden **(yeni veya mevcut** bir projeyi açmana olanak sağlar), En son çözüm veya **Boş** ortam'ı **seçebilirsiniz.**

::: moniker-end

::: moniker range="vs-2017"

## <a name="to-show-a-custom-start-page"></a>Özel bir başlangıç sayfası göstermek için

Visual Studio [](../extensibility/creating-a-custom-start-page.md) SDK'sı kullanarak kendi özel başlangıç sayfanızı oluşturabilir veya başka birinin önceden oluşturduğu bir sayfayı kullanabilirsiniz. Örneğin Market'te özel başlangıç Visual Studio [bulabilirsiniz.](https://marketplace.visualstudio.com/search?target=VS&category=Tools&vsVersion=&subCategory=Start%20Pages&sortBy=Downloads)

Özel bir başlangıç sayfası yüklemek için *.vsix* dosyasını açın veya başlangıç sayfası dosyalarını kopyalayıp *bilgisayarınıza %USERPROFILE%\Documents\Visual Studio 2017\StartPages* klasörüne yapıştırın.

### <a name="to-select-which-custom-start-page-to-display"></a>Hangi özel başlangıç sayfasının görüntülen bir seçim yapmak için

1. Menü çubuğunda Araçlar **Seçenekleri'ne** > **tıklayın.**

1. **Ortam'ı** genişletin ve ardından Başlangıç'ı **seçin.**

1. Başlangıç **Sayfasını Özelleştir** listesinde istediğiniz sayfayı seçin.

> [!TIP]
> Özel bir başlangıç sayfasındaki bir hata Visual Studio kilitlenmeye neden oluyorsa, Visual Studio modunda açabilir ve ardından varsayılan başlangıç sayfasını kullanmak üzere ayarlayabilirsiniz. Bkz. [/SafeMode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca bkz.

- [IDE'Visual Studio kişiselleştirme](../ide/personalizing-the-visual-studio-ide.md)

::: moniker-end

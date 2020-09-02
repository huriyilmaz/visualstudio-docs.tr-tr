---
title: Başlangıç sayfasını özelleştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.startpage
- VS.StartPage.HowDoI
- vs.ToolsOptionsPages.Startup
helpviewer_keywords:
- Start Page [Visual Studio]
- customizing Start Page [Visual Studio]
- Visual Studio Start page
ms.assetid: 925d42eb-ec34-426e-ad81-19db8630e536
caps.latest.revision: 48
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f1c3dfb145e70665156c921cc9a6f740539bc4e6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665845"
---
# <a name="customizing-the-start-page-for-visual-studio"></a>Visual Studio için Başlangıç Sayfasını Özelleştirme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio için başlangıç sayfasını, **Proje Aç** iletişim kutusunu göstermek veya en son yüklenen çözümü açmak gibi birçok varsayılan şekilde özelleştirebilirsiniz. Araç penceresinde çalışan ve Visual Studio'ya özel dahili komutları çalıştıran bir Windows Presentation Foundation (WPF) XAML sayfası olarak, özel bir başlangıç sayfası da gösterebilirsiniz.

## <a name="customizing-the-default-start-page"></a>Varsayılan başlangıç sayfasını özelleştirme

1. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

2. **Ortam**' ı genişletin ve ardından **Başlangıç**' ı seçin.

3. **At başlangıç** listesinde, istediğiniz özelleştirmenin öğesini seçin.

## <a name="show-a-custom-start-page"></a>Özel başlangıç sayfası gösterme

1. Özel bir başlangıç sayfası yüklemek için aşağıdaki yöntemlerden birini kullanın:

    - [Visual Studio Market](https://marketplace.visualstudio.com/), başka bir Web sitesinden veya yerel intranetinizdeki bir sayfadan yüklemeyi yapın.

        > [!NOTE]
        > Visual Studio'nun önceki bir sürümü için hedeflenen bir sayfayı beğeniyorsanız, Visual Studio SDK kullanarak sayfayı yükseltebilirsiniz. Bkz. [nasıl yapılır: Visual Studio özel başlangıç sayfasını yükseltme](../misc/how-to-upgrade-a-visual-studio-custom-start-page.md).

         Özel başlangıç sayfası içeren bir. vsix dosyası açın veya başlangıç sayfası dosyalarını kopyalayıp bilgisayarınızdaki **% USERPROFILE% \Bir Studio 2015 \ StartPages** klasörüne yapıştırın.

    - Visual Studio SDK yüklediyseniz kendi başlangıç sayfanızı oluşturun.

         Bkz. [kendi başlangıç sayfanızı oluşturma](../misc/creating-your-own-start-page.md).

2. Menü çubuğunda **Araçlar**, **Seçenekler**' i seçin.

3. **Ortam**' ı genişletin ve ardından **Başlangıç**' ı seçin.

4. **Başlangıç sayfası Özelleştir** listesinde istediğiniz sayfayı seçin.

> [!NOTE]
> Özel başlangıç sayfasındaki bir hata Visual Studio'nun çökmesine neden olursa, Visual Studio'yu güvenli modda başlatabilir ve varsayılan başlangıç sayfasını kullanacak şekilde ayarlayabilirsiniz. Bkz. [/safemode (devenv.exe)](../ide/reference/safemode-devenv-exe.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio 'Da geliştirme ayarlarını özelleştirme](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3) [kendi başlangıç sayfanızı oluşturma](../misc/creating-your-own-start-page.md)

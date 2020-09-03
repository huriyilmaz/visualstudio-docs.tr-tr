---
title: 'Nasıl yapılır: özel bir başlangıç sayfasını yükseltme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: devlang-csharp
ms.topic: conceptual
ms.assetid: 78342ce6-36c8-485b-a5f6-760e7a420a26
caps.latest.revision: 8
manager: jillfra
ms.openlocfilehash: a7854de705a961463b1e8435e7340548cfc23bf3
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "74293370"
---
# <a name="how-to-upgrade-a-visual-studio-custom-start-page"></a>Nasıl yapılır: Visual Studio özel başlangıç sayfasını yükseltme
Aşağıda listelenen adımları izleyerek Visual Studio 2010 veya Visual Studio 2012 özel başlangıç sayfasını Visual Studio 2015 'e yükseltebilirsiniz.

> [!WARNING]
> Bu yordamda yükseltilen özel başlangıç sayfası, Visual Studio galerisindeki [özel başlangıç sayfası](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.CustomStartPageProjectTemplate) şablonuyla oluşturulmuş olan bir şablondur. Başlangıç sayfanızın yükseltilmesi gereken başka özellikleri olabilir.

### <a name="to-upgrade-a-custom-start-page-to-visual-studio-2015"></a>Özel bir başlangıç sayfasını Visual Studio 2015 'e yükseltmek için

1. Visual Studio 2015 ve Visual Studio 2015 SDK ' nın yüklü olduğundan emin olun. VSSDK 'yi [Microsoft Visual Studio 2013 SDK](https://my.visualstudio.com/Downloads?pid=1436)'dan indirebilirsiniz.

2. Özel şablon projenizi açın. Projenin Yükseltilecek olduğunu bildiren bir ileti görürsünüz. **Tamam** ' a tıklayın ve yükseltmenin tamamlanmasını bekleyin.

3. Başlangıç sayfası projesinin ve denetim projesinin proje özelliklerinde, hedef Framework 'Ün en az .NET Framework 4,5 olduğundan emin olun.

4. Başlangıç sayfası projesinin proje özelliklerinin hata ayıklama kategorisinde, devenv.exe Visual Studio 2015 sürümünün yolunu ayarlayın.

5. Her iki proje için de proje başvuruları ' nda, Microsoft. VisualStudio. Shell. 11.0 başvurularını kaldırın ve Microsoft. VisualStudio. Shell. 14.0 öğesine başvurular ekleyin.

6. XML Düzenleyicisi ile StartPage. xaml ' i açın ve aşağıdaki değişiklikleri yapın:

    1. Ad alanlarını güncelleştirin. Aşağıdaki satırları değiştirin:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.11.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.11.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"
        ```

         şunları yapın:

        ```

        xmlns:vs="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.142.0"
         xmlns:vsfxim="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.Immutable.14.0"
        xmlns:vsfx="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"
        ```

7. MyControl. xaml ' yi açın ve ad alanı başvurusunu `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.11.0"` ile değiştirin `xmlns:vs="clr-namespace:Microsoft.VisualStudio.Shell;assembly=Microsoft.VisualStudio.Shell.14.0"` .
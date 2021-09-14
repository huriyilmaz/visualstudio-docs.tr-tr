---
title: 'Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)'
description: dosya gezgini ' nin ve Windows görev çubuğunun derlenen uygulama için görüntüleyeceği simgeyi belirtmek için ıcon özelliğini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- dotnet
ms.openlocfilehash: 0c03ae786a3fd748177a776b6f2bc2a2e67cb802
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126725760"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)

`Icon`bir projenin özelliği, **dosya gezgini** 'nde ve Windows görev çubuğunda derlenen uygulama için görüntülenecek simge dosyasını (*. ico*) belirler.

`Icon`özelliği, **Project tasarımcısı**'nın **uygulama** bölmesinde erişilebilir; kaynak olarak veya içerik dosyaları olarak bir projeye eklenmiş olan simgelerin bir listesini içerir.

> [!NOTE]
> Bir uygulamanın Icon özelliğini ayarladıktan sonra, `Icon` uygulamadaki her **pencerenin** veya **formun** özelliğini de ayarlayabilirsiniz. tek başına Windows Presentation Foundation (WPF) uygulamaları için pencere simgeleri hakkında daha fazla bilgi için bkz <xref:System.Windows.Window.Icon%2A> . özelliği.

## <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

1. menü çubuğunda **Project**  >  **özellikler**' i seçin.

1. **Project tasarımcı** göründüğünde **uygulama** sekmesini seçin.

1. **(Visual Basic)** &mdash; **Simge** listesinde bir simge (*. ico*) dosyası seçin.

    **C#** &mdash; **Simge** listesinin yakınında, **\<Browse...>** düğmesini seçin ve ardından istediğiniz simge dosyasının konumuna gidin.

## <a name="see-also"></a>Ayrıca bkz.

- [uygulama sayfası, Project tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [uygulama sayfası, Project tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)

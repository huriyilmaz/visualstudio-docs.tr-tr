---
title: 'Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 7e78bd32bf9c21829adeb04a22cd30abb47a3379
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596144"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)

Bir projenin `Icon` özelliği, **Dosya Gezgini** 'Nde ve Windows görev çubuğunda derlenen uygulama için görüntülenecek simge dosyasını ( *. ico*) belirler.

`Icon` özelliğine **Proje Tasarımcısı**'nın **uygulama** bölmesinde erişilebilir; bir projeye kaynak olarak veya içerik dosyaları olarak eklenmiş olan simgelerin bir listesini içerir.

> [!NOTE]
> Bir uygulamanın Icon özelliğini ayarladıktan sonra, uygulamadaki her **pencerenin** veya **formun** `Icon` özelliğini de ayarlayabilirsiniz. Tek başına Windows Presentation Foundation (WPF) uygulamaları için pencere simgeleri hakkında daha fazla bilgi için, bkz. <xref:System.Windows.Window.Icon%2A> özelliği.

## <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

1. Menü çubuğunda, **proje** > **Özellikler**' i seçin.

1. **Proje Tasarımcısı** göründüğünde **uygulama** sekmesini seçin.

1. **(Visual Basic)** **simge** listesinde&mdash;bir simge ( *. ico*) dosyası seçin.

    **C#** **simge** listesinin yakınında &mdash;, **\<gözatmasını seçin... >** düğme ve sonra istediğiniz simge dosyasının konumuna gidin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)

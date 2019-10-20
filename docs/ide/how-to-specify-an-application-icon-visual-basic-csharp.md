---
title: 'Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 1e137eda77f1807b80409872d9fe0c2966df2a41
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656600"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)

Bir projenin `Icon` özelliği, **Dosya Gezgini** 'Nde ve Windows görev çubuğunda derlenen uygulama için görüntülenecek simge dosyasını ( *. ico*) belirler.

@No__t_0 özelliğine **Proje Tasarımcısı**'nın **uygulama** bölmesinde erişilebilir; bir projeye kaynak olarak veya içerik dosyaları olarak eklenmiş olan simgelerin bir listesini içerir.

> [!NOTE]
> Bir uygulamanın Icon özelliğini ayarladıktan sonra, uygulamadaki her **pencerenin** veya **formun** `Icon` özelliğini de ayarlayabilirsiniz. Tek başına Windows Presentation Foundation (WPF) uygulamaları için pencere simgeleri hakkında daha fazla bilgi için, bkz. <xref:System.Windows.Window.Icon%2A> özelliği.

## <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

1. Menü çubuğunda **proje** > **özellikleri**' ni seçin.

1. **Proje Tasarımcısı** göründüğünde **uygulama** sekmesini seçin.

1. **(Visual Basic)** **simge** listesini &mdash;In bir simge ( *. ico*) dosyası seçin.

    **C#** **simge** listesini &mdash;Near **\<Browse seçin... >** düğme ve sonra istediğiniz simge dosyasının konumuna gidin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)
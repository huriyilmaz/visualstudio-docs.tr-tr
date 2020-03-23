---
title: 'Nasıl yapılır: Uygulama simgesini belirtin (Visual Basic, C#)'
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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596144"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl yapılır: Uygulama simgesini belirtin (Visual Basic, C#)

Projenin `Icon` özelliği, **Dosya Gezgini'nde** ve Windows görev çubuğunda derlenen uygulama için görüntülenecek simge dosyasını (*.ico)* belirtir.

Tesise `Icon` **Proje Tasarımcısı'nın** **Uygulama** bölmesinde erişilebilir; bir projeye kaynak olarak veya içerik dosyası olarak eklenen simgelerin listesini içerir.

> [!NOTE]
> Bir uygulama için simge özelliğini ayarladıktan sonra, uygulamadaki her `Icon` **Pencere** veya **Formun** özelliğini de ayarlayabilirsiniz. Windows Presentation Foundation (WPF) bağımsız uygulamaları için pencere simgeleri hakkında bilgi için bkz. <xref:System.Windows.Window.Icon%2A>

## <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. **Çözüm Gezgini'nde**bir proje düğümü **(Çözüm** düğümü değil) seçin.

1. Menü çubuğunda **Project** > **Properties'i**seçin.

1. Proje **Tasarımcısı** göründüğünde, **Uygulama** sekmesini seçin.

1. **(Visual Basic)** &mdash; **Simge** listesinde bir simge (*.ico*) dosyası seçin.

    **C#**&mdash; **Simge** listesinin yakınında, ** \<Gözat...>** düğmesini seçin ve ardından istediğiniz simge dosyasının konumuna göz atın.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Uygulama sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)

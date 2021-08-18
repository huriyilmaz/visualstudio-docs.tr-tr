---
title: 'Nasıl gösterilir: Uygulama simgesi belirtme (Visual Basic, C#)'
description: Simge özelliğini kullanarak derlenmiş uygulama için Dosya Gezgini ve Windows simgesini belirtmeyi öğrenin.
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
ms.openlocfilehash: 0f986be76b22e89d6038e9331da0f2892b866a4425e8324d6f3da963add6ca7c
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121357862"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl gösterilir: Uygulama simgesi belirtme (Visual Basic, C#)

Projenin özelliği, derlenmiş uygulama için Dosya Gezgini görev çubuğunda görüntülenecek simge `Icon` **dosyasını** (*.ico*) Windows belirtir.

özelliğine `Icon` Project **Designer'ın** Uygulama bölmesinden erişilebilir; bir projeye kaynak olarak veya içerik dosyası olarak eklenmiş simgelerin bir listesini içerir. 

> [!NOTE]
> Bir uygulamanın simge özelliğini ayardikten sonra, uygulamanın her `Icon` **Bir Penceresinin** veya **Formun özelliğini** de ayarlayabilirsiniz. Tek başına (WPF) Windows Presentation Foundation pencere simgeleri hakkında bilgi için bkz. <xref:System.Windows.Window.Icon%2A> özelliği.

## <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. Bu **Çözüm Gezgini** proje düğümünü (Çözüm düğümü **değil)** seçin.

1. Menü çubuğunda Özellikler'i **Project**  >  **seçin.**

1. Project **Tasarımcısı** görüntülendiğinde Uygulama **sekmesini** seçin.

1. **(Visual Basic)** &mdash; Simge **listesinde** bir simge (*.ico*) dosyası seçin.

    **C#** &mdash; Simge **listesinin** yanında **\<Browse...>** düğmeyi seçin ve ardından istediğiniz simge dosyasının konumunu bulun.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama sayfası, Project Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Uygulama sayfası, Project Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)

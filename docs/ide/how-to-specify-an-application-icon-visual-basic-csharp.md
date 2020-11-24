---
title: 'Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)'
description: Dosya Gezgini ve Windows görev çubuğunun derlenen uygulama için görüntüleyeceği simgeyi belirtmek için Icon özelliğini nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 34405fd52b49e89c2fa0fc95ec1268448bad3061
ms.sourcegitcommit: d6207a3a590c9ea84e3b25981d39933ad5f19ea3
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/24/2020
ms.locfileid: "95596917"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#)

`Icon`Bir projenin özelliği, **Dosya Gezgini** 'nde ve Windows görev çubuğunda derlenen uygulama için görüntülenecek simge dosyasını (*. ico*) belirler.

`Icon`Özelliği, **Proje Tasarımcısı**'nın **uygulama** bölmesinde erişilebilir; bir projeye kaynak olarak veya içerik dosyaları olarak eklenmiş olan simgelerin bir listesini içerir.

> [!NOTE]
> Bir uygulamanın Icon özelliğini ayarladıktan sonra, `Icon` uygulamadaki her **pencerenin** veya **formun** özelliğini de ayarlayabilirsiniz. Tek başına Windows Presentation Foundation (WPF) uygulamaları için pencere simgeleri hakkında daha fazla bilgi için bkz <xref:System.Windows.Window.Icon%2A> . özelliği.

## <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

1. Menü çubuğunda, **Proje**  >  **özellikleri**' ni seçin.

1. **Proje Tasarımcısı** göründüğünde **uygulama** sekmesini seçin.

1. **(Visual Basic)** &mdash; **Simge** listesinde bir simge (*. ico*) dosyası seçin.

    **C#** &mdash; **Simge** listesinin yakınında, **\<Browse...>** düğmesini seçin ve ardından istediğiniz simge dosyasının konumuna gidin.

## <a name="see-also"></a>Ayrıca bkz.

- [Uygulama sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)
- [Uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)

---
title: 'Nasıl yapılır: uygulama simgesi belirtme (Visual Basic, C#) | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- icons [Visual Studio], application
- application properties [Visual Studio], icons
- application icons [Visual Studio]
ms.assetid: ad8e14ed-adc2-45b6-a0be-818b16d5616f
caps.latest.revision: 21
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 136fd00bea736af0f0c589c28eae597ff8fd558e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72670697"
---
# <a name="how-to-specify-an-application-icon-visual-basic-c"></a>Nasıl Yapılır: Uygulama Simgesi Belirtme (Visual Basic C#)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir projenin `Icon` özelliği, dosya Gezgini 'nde ve Windows görev çubuğunda derlenen uygulama için görüntülenecek simge dosyasını (. ico) belirler.

 @No__t_0 özelliğine **Proje Tasarımcısı**'nın **uygulama** bölmesinde erişilebilir; bir projeye kaynak olarak veya içerik dosyaları olarak eklenmiş olan simgelerin bir listesini içerir.

> [!NOTE]
> Bir uygulamanın Icon özelliğini ayarladıktan sonra, uygulamadaki her **pencerenin** veya **formun** `Icon` özelliğini de ayarlayabilirsiniz. Tek başına Windows Presentation Foundation (WPF) uygulamaları için pencere simgeleri hakkında daha fazla bilgi için, bkz. <xref:System.Windows.Window.Icon%2A> özelliği.

### <a name="to-specify-an-application-icon"></a>Bir uygulama simgesi belirtmek için

1. **Çözüm Gezgini**, bir proje düğümü seçin ( **çözüm** düğümünü değil).

2. Menü çubuğunda, **Proje**, **Özellikler**' i seçin.

3. **Proje Tasarımcısı** göründüğünde **uygulama** sekmesini seçin.

4. **(Visual Basic)** **Simge** listesinde bir simge (. ico) dosyası seçin.

     **C#** **Simge** listesinin yakınında **\<Browse... öğesini seçin. >** düğme ve sonra istediğiniz simge dosyasının konumuna gidin.

## <a name="see-also"></a>Ayrıca Bkz.
 Uygulama [sayfası, proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) [uygulama sayfası, proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md) [uygulama özelliklerini yönetme](../ide/application-properties.md) [nasıl yapılır: kaynak ekleme veya kaldırma](https://msdn.microsoft.com/7b77bc06-3952-4799-b029-def3f8f7f88d)

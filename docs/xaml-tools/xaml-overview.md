---
title: XAML'ye genel bakış
description: XAML ve XAML kod düzenleyicisi hakkında temel bilgileri ve XAML Tasarımcısı araçları Visual Studio.
ms.custom: SEO-VS-2020
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.openlocfilehash: c2bdb5fad308bfcb1f4ec843b88baa937ca77e3c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122045612"
---
# <a name="overview-of-xaml"></a>XAML'ye Genel Bakış

Extensible Application Markup Language (XAML), XML'i temel alan bildirim temelli bir dildir. XAML, kullanıcı arabirimleri oluşturmak için aşağıdaki uygulama türlerinde kapsamlı olarak kullanılır:

- [Windows Presentation Foundation (WPF) uygulamaları](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Evrensel Windows Platformu (UWP) uygulamaları](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms uygulamaları](/xamarin/xamarin-forms/xaml/)

Aşağıdaki XAML kodu basit bir düğme denetimi tanımlar.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML, [workflow Foundation (WF) Windows iş](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml)akışlarını tanımlamak için de kullanılır.

## <a name="xaml-code-editor"></a>XAML kod düzenleyici

Visual Studio IDE'deki [XAML](xaml-code-editor.md) kod düzenleyicisi, Windows platformu ve Xamarin.Forms için WPF ve UWP uygulamaları oluşturmak için ihtiyacınız olan tüm araçları içerir. Ayrıca, Visual Studio'daki IDE 'nin (tümleşik geliştirme ortamı) diğer platformlar için uygulama geliştirmek için kullanabileceğiniz birçok özelliği olsa da, XAML'ye özgü bazı özellikleri de vardır.

## <a name="xaml-designer"></a>XAML Tasarımcısı

Visual Studio ve Visual Studio için Blend [WPF, UWP XAML Tasarımcısı](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) Xamarin.Forms uygulamaları için kullanıcı arabirimleri (UI) derlemeye yardımcı olan bir ağ arabirimi sağlar. Araç Kutusu veya Varlıklar penceresinden denetimleri sürükleyip Özellikler penceresi. Bunu yapmak için Visual Studio Visual Studio için Blend XAML kodunu oluşturun. XAML kodunu doğrudan düzenlemeyi tercih ederseniz bunu da siz de yapabiliriz.

## <a name="whats-new"></a>Yenilikler

En son bilgiler için aşağıdaki kaynaklara bakın:

- **[Visual Studio 2019 sürüm 16.7 Önizleme 1'de XAML](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)** araçlarında geliştirmeler blog gönderisi
- **[Visual Studio 2019'daki XAML geliştirici](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)** araçlarında yapılan Visual Studio blog gönderisi
- **[YouTube'daki yeni Visual Studio XAML](https://youtu.be/yI9OyA4ZM2E)** özellikleri

## <a name="see-also"></a>Ayrıca bkz.

- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin.Forms uygulamaları içinde XAML](/xamarin/xamarin-forms/xaml/)

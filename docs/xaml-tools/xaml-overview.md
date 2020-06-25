---
title: XAML'ye genel bakış
ms.date: 06/23/2020
ms.topic: overview
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: e14e23f9820301374bd435484ba784edf50294bb
ms.sourcegitcommit: 57d96de120e0574e506dfd80bb7adfbac73f96be
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85331945"
---
# <a name="overview-of-xaml"></a>XAML 'ye Genel Bakış

Extensible Application Markup Language (XAML), XML tabanlı bildirim temelli bir dildir. XAML, Kullanıcı arabirimleri oluşturmak için aşağıdaki uygulama türlerinde yaygın olarak kullanılır:

- [Windows Presentation Foundation (WPF) uygulamaları](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [Evrensel Windows Platformu (UWP) uygulamaları](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin. Forms uygulamaları](/xamarin/xamarin-forms/xaml/)

Aşağıdaki XAML kodu bir basit düğme denetimini tanımlar.

```xaml
<Button Click="ButtonClick">Show updates</Button>
```

XAML, [Windows Workflow Foundation (WF) uygulamalarında](/dotnet/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml)iş akışlarını tanımlamak için de kullanılır.

## <a name="xaml-code-editor"></a>XAML kod Düzenleyicisi

Visual Studio IDE 'deki [xaml kod Düzenleyicisi](xaml-code-editor.md) , Windows platformu ve Xamarin. Forms için WPF ve UWP uygulamaları oluşturmak için ihtiyacınız olan tüm araçları içerir. Ayrıca, Visual Studio 'daki IDE (tümleşik geliştirme ortamı), diğer platformlar için uygulama geliştirmek üzere kullanabileceğiniz birçok özelliğe sahiptir, ancak XAML için de benzersiz olan bazı özellikler de vardır.

## <a name="xaml-designer"></a>XAML Tasarımcısı

Visual Studio ve Visual Studio için Blend WPF, UWP ve Xamarin. Forms uygulamaları için Kullanıcı arabirimleri (UI) oluşturmanıza yardımcı olan bir [XAML Tasarımcısı](creating-a-ui-by-using-xaml-designer-in-visual-studio.md) sağlar. Denetimleri araç kutusu veya varlıklar penceresinden sürükleyebilir ve Özellikler penceresi özellikleri ayarlayabilirsiniz. Bunu yaptığınızda, Visual Studio ve Visual Studio için Blend karşılık gelen XAML kodunu oluşturun. XAML kodunu doğrudan düzenlemeyi tercih ediyorsanız, bunu da yapabilirsiniz.

## <a name="whats-new"></a>Yenilikler

En son bilgiler için aşağıdaki kaynaklara bakın:

- **[Visual Studio 2019 sürüm 16,7 Preview 1 blog GÖNDERISINE XAML araçları geliştirmeleri](https://devblogs.microsoft.com/visualstudio/improvements-to-xaml-tooling-in-visual-studio-2019-version-16-7-preview-1/)**
- **[Visual Studio 2019 blog gönderisinden xaml geliştirici araçlarındaki](https://devblogs.microsoft.com/visualstudio/whats-new-in-xaml-developer-tools-in-visual-studio-2019-for-wpf-uwp/)** yenilikler
- YouTube 'daki **[Visual Studio videosunun yenı xaml özellikleri](https://youtu.be/yI9OyA4ZM2E)**

## <a name="see-also"></a>Ayrıca bkz.

- [WPF uygulamalarında XAML](/dotnet/framework/wpf/advanced/xaml-in-wpf)
- [UWP uygulamalarında XAML](/windows/uwp/xaml-platform/xaml-overview)
- [Xamarin. Forms uygulamalarındaki XAML](/xamarin/xamarin-forms/xaml/)

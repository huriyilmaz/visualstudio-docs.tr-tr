---
title: Tema oluşturma
description: Araç pencerelerini ve diğer XAML denetimlerini, temanın renk temaları Visual Studio şekilde düzgün bir şekilde tema.
ms.date: 12/01/2021
ms.topic: conceptual
author: madskristensen
ms.author: madsk
manager: pchapman
ms.prod: visual-studio-windows
ms.technology: vs-ide-sdk
ms.custom: cookbook
ms.openlocfilehash: 1a33a6557d8f42a33f32faea38880cd95efcc70b
ms.sourcegitcommit: a149b3a034bb555ad217656c0ec8bc1672b1e215
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/03/2021
ms.locfileid: "133516692"
---
# <a name="matching-visual-studio-themes-in-visual-studio-extensions"></a>Visual Studio uzantılarında Visual Studio temalarını eşleştirme

WPF kullanarak herhangi bir özel kullanıcı arabirimi 7.000.000'den fazla kullanıcı arabirimi Visual Studio. Bu şekilde kullanıcı arabiriminiz yerel gibi Visual Studio. Yoksa, araç pencereniz ve iletişim kutularınız Açık temada aşağıdaki gibi görünür:

:::image type="content" source="../media/theming-light-none.png" alt-text="Açık temada temasız kullanıcı arabirimi.":::

Metin kutularının ve düğmelerin çevresindeki doldurmanın nasıl doğru olmadığını fark mı ettiniz? Koyu temada daha da kötüleşiyor:

:::image type="content" source="../media/theming-dark-none.png" alt-text="Koyu temada temasız kullanıcı arabirimi.":::

Artık metin ve arka plan renkleri, okumayı neredeyse imkansız hale geliyor. İyi değil.

Kullanıcı arabirimimizin arka plan renklerinin, düğme stil oluşturmanın vb. basit bir Visual Studio olduğundan emin olmak için kolay bir yol vardır. Bu şekilde aynı kullanıcı arabirimi Açık temada aşağıdaki gibi olabilir:

:::image type="content" source="../media/theming-light.png" alt-text="Açık temada doğru temaya sahip kullanıcı arabirimi.":::

Veya Koyu temada:

:::image type="content" source="../media/theming-dark.png" alt-text="Koyu temada doğru temaya sahip kullanıcı arabirimi.":::

Bu çok daha iyi görünüyor. Şimdi kullanıcı arabirimimizin temasını nasıl alalıymıza bakalım.

## <a name="wpf-usercontrol"></a>WPF UserControl
Burada, doğrudan bir araç penceresinin `<UserControl>` içinde kullanılmaktadır.

```xml
<UserControl x:Class="TestExtension.RunnerWindowControl"
             xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
             xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
             xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
             xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
             xmlns:toolkit="clr-namespace:Community.VisualStudio.Toolkit;assembly=Community.VisualStudio.Toolkit"
             toolkit:Themes.UseVsTheme="True">
```

İçeri aktarılan `xmlns:toolkit` ad alanına ve özniteliğine dikkat `toolkit:Themes.UseVsTheme="True"` et. Kendi kullandığı WPF denetimleri için resmi stili otomatik Visual Studio uygulanır. Stilin tamamının uygulanması için başka bir şey yapmak zorunda `<UserControl>` değil. Kolay!

Bir diğer avantaj da kullanıcı renk temasını Açıktan Koyuya değiştirse kullanıcı arabirimimizin yeniden yüklemeye gerek kalmadan hemen geçiş yapmaktır.

## <a name="dialogwindow-control"></a>DialogWindow denetimi
Visual Studio, denetim olan özel pencereler için kullanabileceğimiz bir denetimle `DialogWindow` birlikte kullanılabilir. Bunu herhangi bir iletişim kutusu pencereleri için kullanmanız önerilir, ancak araç pencereleri içinde de kullanılabilir.

Diğer XAML pencere türlerine çok benzer.

```xml
<platform:DialogWindow 
    x:Class="TestExtension.ThemeWindowDialog"
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
    xmlns:platform="clr-namespace:Microsoft.VisualStudio.PlatformUI;assembly=Microsoft.VisualStudio.Shell.15.0"
    xmlns:toolkit="clr-namespace:Community.VisualStudio.Toolkit;assembly=Community.VisualStudio.Toolkit"
    toolkit:Themes.UseVsTheme="True">
```

Hem araç seti hem de platform ve özniteliği için içe aktarılan ad alanlarına dikkat `toolkit:Themes.UseVsTheme="True"` edin.

İşte bu kadar kolay. İletişim kutusu pencereniz artık farklı renkler ve Visual Studio kullanılarak renkle gösterilir.

## <a name="get-the-source-code"></a>Kaynak kodunu alma
Bu uzantının kaynak kodunu [Toolkit test projesinde Community bulabilirsiniz.](https://github.com/VsixCommunity/Community.VisualStudio.Toolkit/tree/master/test/VSSDK.TestExtension)

## <a name="additional-resources"></a>Ek kaynaklar
Bu kaynaklara sahip Visual Studio hakkında daha fazla bilgi.

* [Visual Studio için renkler ve stil Visual Studio](../../ux-guidelines/colors-and-styling-for-visual-studio.md)
* [Visual Studio için paylaşılan renkler](../../ux-guidelines/shared-colors-for-visual-studio.md)
* [Renk değeri başvurusu](../../ux-guidelines/color-value-reference-for-visual-studio.md)

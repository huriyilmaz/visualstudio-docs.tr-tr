---
title: WPF XAML Çalışırken Yeniden Yükleme UWP uygulamaları için uygulama
description: XAML Çalışırken Yeniden Yükleme veya XAML düzenle ve devam edin, uygulamaları çalışırken XAML kodunuz üzerinde değişiklik yapmanızı sağlar
ms.date: 12/08/2021
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.custom: contperf-fy22q1
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 7784bfd0f1653b66f52cf3435adac54e79ffd232
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366819"
---
# <a name="what-is-xaml-hot-reload-for-wpf-and-uwp-apps-visual-studio"></a>WPF XAML Çalışırken Yeniden Yükleme UWP uygulamaları için nasıl bir uygulamadır? (Visual Studio)

Bu XAML Çalışırken Yeniden Yükleme, WPF ve UWP uygulamalarınız için XAML kodunu artımlı olarak derleme ve test edin. Bunu, çalışan uygulamanın veri bağlamı, kimlik doğrulama durumu ve tasarım zamanında benzetimini yapmak zor olan diğer gerçek dünya karmaşıklıkları sayesinde de kullanabilirsiniz.

> [!TIP]
> Kullanıcı arabirimini (UI) kullanarak buraya XAML Çalışırken Yeniden Yükleme hoş geldiniz! Bu konuda daha fazla bilgi edinmek için doğru XAML Çalışırken Yeniden Yükleme.
>
> Ancak sorun giderme adımlarıyla ilgili yardım için XAML Çalışırken Yeniden Yükleme sorun giderme XAML Çalışırken Yeniden Yükleme [bakın.](xaml-hot-reload-troubleshooting.md)


## <a name="where-to-get-xaml-hot-reload"></a>Nereden XAML Çalışırken Yeniden Yükleme

Visual Studio XAML Çalışırken Yeniden Yükleme şu anda yalnızca bir uygulamayı Visual Studio -veya- **Visual Studio için Blend** ekli  (**F5** veya Hata ayıklamayı başlat ) **ile çalıştırarak çalıştırarak desteklemektedir.** 

El ile bir ortam değişkeni ayarlamadıkça [İşleme ekle'yi](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) [kullanarak bu deneyimi etkinleştirebilirsiniz.](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)


## <a name="applications-for-xaml-hot-reload"></a>XAML Çalışırken Yeniden Yükleme için uygulamalar

XAML Çalışırken Yeniden Yükleme özellikle şu senaryolarda yararlıdır:

* Uygulama hata ayıklama modunda başlatıldıktan sonra XAML kodunda bulunan kullanıcı arabirimi sorunlarını düzeltme.

* Geliştirme aşamasında olan bir uygulama için yeni bir kullanıcı arabirimi bileşeni oluşturma ve uygulamanın çalışma zamanı bağlamından yararlanma.

## <a name="supported-os"></a>Desteklenen İşletim Sistemi

|Desteklenen Uygulama Türleri|İşletim Sistemi ve Araçlar|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ ve .NET Core</br>Windows 7 ve sonrası |
|Evrensel Windows uygulamaları (UWP)|Windows 10 SDK 14393+ [ve Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ve sonraki bir sürümü ile|

**Xamarin.Forms kullanıyorsanız bkz.** [Xamarin.Forms XAML Çalışırken Yeniden Yükleme için bkz.](/xamarin/xamarin-forms/xaml/hot-reload).

## <a name="example"></a>Örnek 

Aşağıdaki animasyonda, Canlı Görsel Ağaç kullanarak bazı kaynak kodu açma ve ardından bir düğmenin XAML Çalışırken Yeniden Yükleme rengini değiştirmek için XAML Çalışırken Yeniden Yükleme kullanma örneği gösterir.

:::image type="content" source="media/vs-2022/xaml-hot-reload-live-visual-tree.gif" alt-text="Canlı Görsel Ağaç'ın kaynak kodu açma ve kullanıcı arabirimi öğelerini XAML Çalışırken Yeniden Yükleme kullanma animasyonu.":::

## <a name="see-also"></a>Ayrıca bkz.

* [XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme](xaml-hot-reload-troubleshooting.md)
* [Xamarin.Forms için XAML Çalışırken Yeniden Yükleme](/xamarin/xamarin-forms/xaml/hot-reload)
* [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

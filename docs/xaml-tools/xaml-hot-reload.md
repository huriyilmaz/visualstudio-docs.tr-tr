---
title: XAML Sıcak Yeniden Yükleme kullanarak XAML yazın ve hata ayıklama
description: XAML Hot Reload veya XAML'yi edin ve devam edin, uygulamaları çalıştırırken XAML kodunuzda değişiklik yapmanızı sağlar
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880095"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Visual Studio'da XAML Hot Reload ile XAML kodunu çalıştıran yazma ve hata ayıklama

XAML Hot Reload, uygulamanız çalışırken XAML kodunda değişiklik yapmanıza izin vererek WPF veya UWP uygulaması kullanıcı arabiriminizi (UI) oluşturmanıza yardımcı olur. Hot Reload Visual Studio ve Blend for Visual Studio'da mevcuttur. Bu özellik, xaml kodunu çalışan uygulamanın veri bağlamı, kimlik doğrulama durumu ve tasarım süresi boyunca simüle edilmesi zor olan diğer gerçek dünya karmaşıklığının yararına aşamalı olarak oluşturmanızı ve test etmenizi sağlar. Sorun giderme sorunu Giderme XAML Hot Reload yardıma ihtiyacınız varsa, bunun yerine [Sorun Giderme XAML Sıcak Reload](xaml-hot-reload-troubleshooting.md) bakın.

> [!NOTE]
> Xamarin.Forms kullanıyorsanız, [Xamarin.Forms için XAML Sıcak Yeniden Yükleme](/xamarin/xamarin-forms/xaml/hot-reload)bakın.

XAML Hot Reload özellikle bu senaryolarda yararlıdır:

* Uygulama hata ayıklama modunda başlatıldıktan sonra XAML kodunuzda bulunan UI sorunlarını giderme.

* Uygulamanızın çalışma zamanı bağlamından yararlanırken geliştirilmekte olan bir uygulama için yeni bir Ara Bilgi bileşeni oluşturma.

|Desteklenen Uygulama Türleri|İşletim Sistemi ve Araçları|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ ve .NET Çekirdek</br>Windows 7 ve üzeri |
|Evrensel Windows uygulamaları (UWP)|Windows 10 ve üzeri, [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393+ ile |

Aşağıdaki resimde, kaynak kodunuzu açmak için Canlı Görsel Ağaç ve ardından düğme metnini ve düğme rengini değiştirmek için XAML Hot Reload'ın kullanımı gösterilmektedir.

![XAML Çalışırken Yeniden Yükleme](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Hot Reload şu anda yalnızca Visual Studio veya Blend for Visual Studio'da uygulamanızı ses hata ayıklayıcı **(F5** veya **Start hata ayıklama)** ile çalıştırırken desteklenir. Bir [ortam değişkenini el ile ayarlamadığınız](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process) [sürece, işlemek için Ekle'yi](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) kullanarak bu deneyimi etkinleştiremezsiniz.

## <a name="known-limitations"></a>Bilinen sınırlamalar

XAML Hot Reload'ın bilinen sınırlamaları aşağıda veda edilebistir. Girdiğiniz herhangi bir sınırlamayı aşmak için hata ayıklamaişlemini durdurmanız ve ardından işlemi tamamlamanız.

|Sınırlama|WPF|UWP|Notlar|
|-|-|-|-|
|Uygulama çalışırken olayları kontrol etmek için kablolama|Desteklenmiyor|Desteklenmiyor|Bkz. hata: *Olay Başarısız olduğundan emin olun.* WPF'de varolan bir olay işleyicisi başvuruda bulunabilirsiniz unutmayın. UWP uygulamalarında, varolan bir olay işleyicisi başvurudesteklenmez.|
|Uygulamanızın Sayfasında/Penceresinde veya *App.xaml'daki* gibi kaynak sözlüğünde kaynak nesneleri oluşturma|Visual Studio 2019 Güncelleme 2'de başlayan desteklendi|Destekleniyor|Örnek: kaynak `SolidColorBrush` sözlüğüne bir kaynak `StaticResource`sözlüğüne bir .</br>Not: XAML Hot Reload kullanılırken kaynak sözlüğüne yazılan statik kaynaklar, stil dönüştürücüler ve diğer öğeler uygulanabilir/kullanılabilir. Yalnızca kaynağın oluşturulması desteklenmez.</br> Kaynak sözlüğü `Source` özelliğini değiştirme.|
|Uygulama çalışırken projenize yeni denetimler, sınıflar, pencereler veya diğer dosyalar ekleme|Desteklenmiyor|Desteklenmiyor|None|
|NuGet paketlerini yönetme (paketleri ekleme/kaldırma/güncelleme)|Desteklenmiyor|Desteklenmiyor|None|
|{x:Bind} biçimlendirme uzantısını kullanan veri bağlamayı değiştirme|Yok|Visual Studio 2019'dan itibaren desteklendi|Bunun için Windows 10 sürüm 1809 (derleme 10.0.17763) gerekiyor. Visual Studio 2017 veya önceki sürümlerinde desteklenmez.|
|X:Uid yönergelerinin değiştirilmesi desteklenmiyor|Yok|Desteklenmiyor|None|
|Birden çok işlem | Desteklenmiyor | Desteklenmiyor | Sıcak yeniden yükleme bir seferde yalnızca 1 prosese karşı kullanılabilir. |

## <a name="error-messages"></a>Hata iletileri

XAML Hot Reload kullanırken aşağıdaki hatalarla karşılaşabilirsiniz.

|Hata iletisi|Açıklama|
|-|-|
|Etkinin Başarısız Olduğundan Emin Olun|Hata, bir olayı denetimlerinizden birine havale etmeye çalıştığınızı ve uygulamanız çalışırken desteklenmediğinizi gösterir.|
|Bu değişiklik XAML Hot Reload tarafından desteklenmez ve hata ayıklama oturumu sırasında uygulanmaz.|Hata, denediğiniz değişikliğin XAML Hot Reload tarafından desteklenmediğini gösterir. Hata ayıklama oturumunu durdurun, değişikliği yapın ve sonra hata ayıklama oturumunu yeniden başlatın. Desteklenen görmek istediğiniz desteklenmeyen bir senaryo bulursanız, [Visual Studio Developer Community'deki](https://developercommunity.visualstudio.com/spaces/8/index.html)yeni "Özellik öner" seçeneğimizi kullanın. |

## <a name="see-also"></a>Ayrıca bkz.

* [XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme](xaml-hot-reload-troubleshooting.md)
* [Xamarin.Forms için XAML Sıcak Reload](/xamarin/xamarin-forms/xaml/hot-reload)
* [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

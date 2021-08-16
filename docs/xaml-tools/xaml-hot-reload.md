---
title: XAML Çalışırken Yeniden Yükleme kullanarak XAML yazma ve hata XAML Çalışırken Yeniden Yükleme
description: XAML Çalışırken Yeniden Yükleme veya XAML düzenle ve devam edin, uygulamaları çalışırken XAML kodunuz üzerinde değişiklik yapmanızı sağlar
ms.date: 09/23/2020
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: 50fa8c216da426172a30d7b3b1adf2254dad4e28adeac9b05055de5e9bfa094b
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121351529"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Visual Studio'de XAML Çalışırken Yeniden Yükleme ile XAML kodu Visual Studio

XAML Çalışırken Yeniden Yükleme çalışırken XAML kodunda değişiklik yapmanıza izin vererek WPF veya UWP uygulaması kullanıcı arabiriminizi (UI) derlemenize yardımcı olur. Çalışırken Yeniden Yükleme hem Visual Studio hem de Visual Studio için Blend. Bu özellik, çalışan uygulamanın veri bağlamı, kimlik doğrulama durumu ve tasarım zamanında benzetimini yapmak zor olan diğer gerçek dünya karmaşıklığının avantajıyla XAML kodunu artımlı olarak derlemeye ve teste olanak sağlar. Sorun giderme adımlarıyla ilgili yardıma ihtiyacınız XAML Çalışırken Yeniden Yükleme, bunun [yerine sorun XAML Çalışırken Yeniden Yükleme](xaml-hot-reload-troubleshooting.md) bakın.

> [!NOTE]
> Xamarin.Forms kullanıyorsanız bkz. [Xamarin.Forms için XAML Çalışırken Yeniden Yükleme.](/xamarin/xamarin-forms/xaml/hot-reload)

XAML Çalışırken Yeniden Yükleme bu senaryolarda özellikle yararlıdır:

* Uygulama hata ayıklama modunda başlatıldıktan sonra XAML kodunda bulunan kullanıcı arabirimi sorunlarını düzeltme.

* Geliştirme aşamasında olan bir uygulama için yeni bir kullanıcı arabirimi bileşeni oluşturma ve uygulamanın çalışma zamanı bağlamından yararlanma.

|Desteklenen Uygulama Türleri|İşletim Sistemi ve Araçlar|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ ve .NET Core</br>Windows 7 ve üzeri |
|Evrensel Windows uygulamaları (UWP)|Windows 10 SDK 14393+ [ile Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) ve üzeri |

Aşağıdaki çizimde, kaynak kodunuzu açmak için Canlı Görsel Ağaç kullanımı ve ardından XAML Çalışırken Yeniden Yükleme ve düğme rengini değiştirme adımları gösterilmiştir.

![XAML Çalışırken Yeniden Yükleme](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Çalışırken Yeniden Yükleme şu anda yalnızca, Visual Studio veya Visual Studio için Blend ekli (**F5** veya Hata ayıklamayı başlat) ile birlikte **çalıştırıldı.** El ile bir ortam değişkeni ayarlamadıkça [İşleme ekle'yi](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) [kullanarak bu deneyimi etkinleştirebilirsiniz.](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)

## <a name="known-limitations"></a>Bilinen sınırlamalar

Aşağıdakiler, bilinen XAML Çalışırken Yeniden Yükleme. Karşılaşacak herhangi bir sınırlamaya çözüm olarak hata ayıklayıcıyı durdurmanız ve ardından işlemi tamamlamanız gerekir.

|Sınırlama|WPF|UWP|Notlar|
|-|-|-|-|
|Uygulama çalışırken olayları denetimlere kablolama|Desteklenmiyor|Desteklenmez|Hataya bakın: *Olayın Başarısız Olduğundan Emin Oldu.* WPF'de mevcut bir olay işleyiciye başvurabilirsiniz. UWP uygulamaları için mevcut bir olay işleyiciye başvuru desteklenmiyor.|
|Kaynak sözlüğünde, uygulamanın Sayfa/Pencere veya *App.xaml'sinde* bulunanlar gibi kaynak nesneleri oluşturma|Visual Studio 2019 Güncelleştirme 2'den itibaren desteklemektedir|Desteklenir|Örnek: olarak `SolidColorBrush` kullanmak üzere bir kaynak sözlüğüne `StaticResource` ekleme.</br>Not: Statik kaynaklar, stil dönüştürücüler ve kaynak sözlüğüne yazılan diğer öğeler, kaynak sözlüğünü kullanırken XAML Çalışırken Yeniden Yükleme. Yalnızca kaynağın oluşturulması desteklenmiyor.</br> Kaynak sözlüğü özelliğini `Source` değiştirme.|
|Uygulama çalışırken projenize yeni denetimler, sınıflar, pencereler veya diğer dosyalar ekleme|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|Paket NuGet yönetme (paket ekleme/kaldırma/güncelleştirme)|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|{x:Bind} işaretleme uzantısını kullanan veri bağlamayı değiştirme|Yok|Visual Studio 2019'dan itibaren destekle|Bunun için Windows 10 1809 (derleme 10.0.17763) gerekir. 2017 Visual Studio önceki sürümlerde desteklenmiyor.|
|x:Uid yönergelerini değiştirme desteklenmiyor|Yok|Desteklenmiyor|Hiçbiri|
|Birden çok işlem | Desteklenir | Desteklenir | Visual Studio 2019 [sürüm 16.6 ve sonraki sürümlerde](/visualstudio/releases/2019/release-notes-v16.6) destekle |

## <a name="error-messages"></a>Hata iletileri

Uygulama kullanırken aşağıdaki hatalara XAML Çalışırken Yeniden Yükleme.

|Hata iletisi|Açıklama|
|-|-|
|Olayın Başarısız Olduğundan Emin Olmak|Hata, bir olayı denetimlerinden biri ile bağlantıya çalıştığınıza işaret ediyor ve bu durum uygulama çalışırken desteklenmiyor.|
|Bu değişiklik uygulama tarafından XAML Çalışırken Yeniden Yükleme ve hata ayıklama oturumu sırasında uygulanmaz.|Hata, yapmaya çalıştığınız değişikliğin uygulama tarafından destek XAML Çalışırken Yeniden Yükleme. Hata ayıklama oturumunu durdurun, değişikliğin ardından hata ayıklama oturumunu yeniden başlatın. Destekleneni görmek istediğiniz desteklenmeyen bir senaryo bulursanız, Visual Studio [Developer](https://aka.ms/feedback/suggest?space=8)Community . |

## <a name="see-also"></a>Ayrıca bkz.

* [XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme](xaml-hot-reload-troubleshooting.md)
* [Xamarin.Forms için XAML Çalışırken Yeniden Yükleme](/xamarin/xamarin-forms/xaml/hot-reload)
* [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

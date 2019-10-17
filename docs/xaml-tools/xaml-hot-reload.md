---
title: XAML 'yi dinamik yeniden yükleme kullanarak yazma ve hata ayıklama
description: XAML çalışırken yeniden yükleme veya XAML düzenleme ve devam etme, uygulamaları çalıştırırken XAML kodunuzda değişiklik yapmanıza olanak sağlar
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: f1232620d40a26c894b6b2f38fc7d8c10a44c405
ms.sourcegitcommit: 485ffaedb1ade71490f11cf05962add1718945cc
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/16/2019
ms.locfileid: "72450935"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Visual Studio 'da XAML etkin yeniden yüklemesine sahip XAML kodunu yazma ve hata ayıklama

XAML çalışırken yeniden yükleme, uygulamanızın çalışırken XAML kodunda değişiklik yapmanıza izin vererek WPF veya UWP uygulama kullanıcı arabirimi (UI) oluşturmanıza yardımcı olur. Dinamik yeniden yükleme, hem Visual Studio hem de Visual Studio için Blend kullanılabilir. Bu özellik, çalışan uygulamanın veri bağlamının, kimlik doğrulama durumunun ve tasarım zamanı sırasında benzetim yapmak zor olan diğer gerçek hayklığın avantajıyla XAML kodunu artımlı olarak derleyip test etmenizi sağlar. XAML dinamik yeniden yükleme sorunlarını gidermek için yardıma ihtiyacınız varsa bkz. bunun yerine [xaml etkin yeniden yükleme sorunlarını giderme](xaml-hot-reload-troubleshooting.md) .

> [!NOTE]
> Xamarin. Forms kullanıyorsanız, bkz. [Xamarin. Forms Için xaml etkin yeniden yükleme](/xamarin/xamarin-forms/xaml/hot-reload).

XAML dinamik yeniden yükleme, özellikle bu senaryolarda yararlı olur:

* Uygulama hata ayıklama modunda başlatıldıktan sonra XAML kodunuzda bulunan Kullanıcı arabirimi sorunlarını düzeltme.

* Uygulamanın çalışma zamanı bağlamından yararlanarak geliştirme aşamasındaki bir uygulama için yeni bir kullanıcı arabirimi bileşeni oluşturma.

|Desteklenen uygulama türleri|İşletim sistemi ve araçlar|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + ve .NET Core</br>Windows 7 ve üzeri |
|Evrensel Windows uygulamaları (UWP)|Windows 10 ve üzeri, [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

Aşağıdaki çizim, kaynak kodunuzu açmak için canlı görsel ağaç kullanımını ve sonra düğme metnini ve düğme rengini değiştirmek için XAML etkin yeniden yüklemeyi gösterir.

![XAML Çalışırken Yeniden Yükleme](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML etkin yeniden yüklemesi şu anda yalnızca Visual Studio 'da uygulamanızı çalıştırırken veya hata ayıklayıcı ekli olarak Visual Studio için Blend desteklenir (**F5** veya **hata ayıklamayı Başlat**). [Bir ortam değişkenini el ile](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)ayarlamadığınız sürece, [İşleme İliştir](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) ' i kullanarak bu deneyimi etkinleştiremezsiniz.

## <a name="known-limitations"></a>Bilinen sınırlamalar

XAML sık yeniden yükleme 'nin bilinen kısıtlamaları aşağıda verilmiştir. ' De çalıştırdığınız herhangi bir sınırlamaya geçici bir çözüm bulmak için, hata ayıklayıcıyı durdurmanız ve sonra işlemi doldurmanız yeterlidir.

|Sınırlama|WPF|UWP|Notlar|
|-|-|-|-|
|Uygulama çalışırken denetimlere yönelik bağlantı olayları|Desteklenmez|Desteklenmez|Bkz. hata: *olayın başarısız olduğundan emin olun*. WPF 'de, var olan bir olay işleyicisine başvurabilirsiniz. UWP uygulamalarında, var olan bir olay işleyicisine başvurulması desteklenmez.|
|Uygulamanızın sayfa/pencere veya *app. xaml* gibi bir kaynak sözlüğünde kaynak nesneleri oluşturma|Visual Studio 2019 güncelleştirme 2 ' den itibaren desteklenir|Desteklenir|Örnek: `StaticResource` olarak kullanmak için bir kaynak sözlüğüne `SolidColorBrush` ekleme.</br>Note: statik kaynaklar, stil dönüştürücüler ve bir kaynak sözlüğüne yazılan diğer öğeler XAML etkin yeniden yükleme kullanılırken uygulanabilir/kullanılabilir. Yalnızca kaynağın oluşturulması desteklenmez.</br> Kaynak sözlüğünü değiştirme `Source` özelliği.|
|Uygulama çalışırken projenize yeni denetimler, sınıflar, pencereler veya diğer dosyalar ekleme|Desteklenmez|Desteklenmez|Yok.|
|NuGet paketlerini yönetme (paket ekleme/kaldırma/güncelleştirme)|Desteklenmez|Desteklenmez|Yok.|
|{X:Bind} biçimlendirme uzantısını kullanan veri bağlamasını değiştirme|Yok|Visual Studio 2019 ' den itibaren desteklenir|Bu, Windows 10 sürüm 1809 (derleme 10.0.17763) gerektirir. Visual Studio 2017 veya önceki sürümlerde desteklenmez.|
|X:Uid yönergelerinin değiştirilmesi desteklenmiyor|Yok|Desteklenmez|Yok.|

## <a name="error-messages"></a>Hata iletileri

XAML sık yükleme 'yi kullanırken aşağıdaki hatalarda gelebiliriz.

|Hata iletisi|Açıklama|
|-|-|
|Olayın başarısız olduğundan emin olun|Hata, sizin uygulamanız çalışırken desteklenmeyen denetimlerinizin birine bir olay gönderilmeye çalıştığınız anlamına gelir.|
|Bu değişiklik XAML Hot Reload tarafından desteklenmiyor ve hata ayıklama oturumu sırasında uygulanmayacak.|Hata, denediğiniz değişikliğin XAML etkin yeniden yükleme tarafından desteklenmediğini gösterir. Hata ayıklama oturumunu durdurun, değişikliği yapın ve hata ayıklama oturumunu yeniden başlatın. Desteklendiğini görmek istediğiniz desteklenmeyen bir senaryo bulursanız, [Visual Studio Geliştirici topluluğu](https://developercommunity.visualstudio.com/spaces/8/index.html)'nda yeni "özellik öner" seçeneğini kullanın. |

## <a name="see-also"></a>Ayrıca bkz.

* [XAML dinamik yeniden yükleme sorunlarını giderme](xaml-hot-reload-troubleshooting.md)
* [Xamarin. Forms için XAML Hot reload](/xamarin/xamarin-forms/xaml/hot-reload)
* [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

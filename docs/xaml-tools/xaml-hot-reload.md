---
title: XAML 'yi dinamik yeniden yükleme kullanarak yazma ve hata ayıklama
description: XAML çalışırken yeniden yükleme veya XAML düzenleme ve devam etme, uygulamaları çalıştırırken XAML kodunuzda değişiklik yapmanıza olanak sağlar
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
ms.openlocfilehash: 4baea5effc0670a8366074187475c7c09c5b39ef
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122130279"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Visual Studio xaml üzerinde çalışan XAML kodu yazma ve hata ayıklama

XAML çalışırken yeniden yükleme, uygulamanızın çalışırken XAML kodunda değişiklik yapmanıza izin vererek WPF veya UWP uygulama kullanıcı arabirimi (UI) oluşturmanıza yardımcı olur. sık yeniden yükleme, hem Visual Studio hem de Visual Studio için Blend kullanılabilir. Bu özellik, çalışan uygulamanın veri bağlamının, kimlik doğrulama durumunun ve tasarım zamanı sırasında benzetim yapmak zor olan diğer gerçek hayklığın avantajıyla XAML kodunu artımlı olarak derleyip test etmenizi sağlar. XAML dinamik yeniden yükleme sorunlarını gidermek için yardıma ihtiyacınız varsa bkz. bunun yerine [xaml etkin yeniden yükleme sorunlarını giderme](xaml-hot-reload-troubleshooting.md) .

> [!NOTE]
> Xamarin. Forms kullanıyorsanız, bkz. [Xamarin. Forms Için xaml etkin yeniden yükleme](/xamarin/xamarin-forms/xaml/hot-reload).

XAML dinamik yeniden yükleme, özellikle bu senaryolarda yararlı olur:

* Uygulama hata ayıklama modunda başlatıldıktan sonra XAML kodunuzda bulunan Kullanıcı arabirimi sorunlarını düzeltme.

* Uygulamanın çalışma zamanı bağlamından yararlanarak geliştirme aşamasındaki bir uygulama için yeni bir kullanıcı arabirimi bileşeni oluşturma.

|Desteklenen uygulama türleri|İşletim sistemi ve araçlar|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + ve .net Core</br>Windows 7 ve üzeri |
|evrensel Windows uygulamaları (UWP)| [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + ile Windows 10 ve üzeri |

Aşağıdaki çizim, kaynak kodunuzu açmak için canlı görsel ağaç kullanımını ve sonra düğme metnini ve düğme rengini değiştirmek için XAML etkin yeniden yüklemeyi gösterir.

![XAML Çalışırken Yeniden Yükleme](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML etkin yeniden yüklemesi şu anda yalnızca uygulamanız Visual Studio veya hata ayıklayıcı ekli Visual Studio için Blend çalıştırılırken desteklenir (**F5** veya **hata ayıklamayı başlat**). [Bir ortam değişkenini el ile](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)ayarlamadığınız sürece, [İşleme İliştir](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) ' i kullanarak bu deneyimi etkinleştiremezsiniz.

## <a name="known-limitations"></a>Bilinen sınırlamalar

XAML sık yeniden yükleme 'nin bilinen kısıtlamaları aşağıda verilmiştir. ' De çalıştırdığınız herhangi bir sınırlamaya geçici bir çözüm bulmak için, hata ayıklayıcıyı durdurmanız ve sonra işlemi doldurmanız yeterlidir.

|Sınırlama|WPF|UWP|Notlar|
|-|-|-|-|
|Uygulama çalışırken denetimlere yönelik bağlantı olayları|Desteklenmiyor|Desteklenmez|Bkz. hata: *olayın başarısız olduğundan emin olun*. WPF 'de, var olan bir olay işleyicisine başvurabilirsiniz. UWP uygulamalarında, var olan bir olay işleyicisine başvurulması desteklenmez.|
|Uygulamanızın sayfa/pencere veya *app. xaml* gibi bir kaynak sözlüğünde kaynak nesneleri oluşturma|Visual Studio 2019 güncelleştirme 2 ' den itibaren desteklenir|Desteklenir|Örnek: `SolidColorBrush` olarak kullanmak için bir kaynak sözlüğüne ekleme `StaticResource` .</br>Note: statik kaynaklar, stil dönüştürücüler ve bir kaynak sözlüğüne yazılan diğer öğeler XAML etkin yeniden yükleme kullanılırken uygulanabilir/kullanılabilir. Yalnızca kaynağın oluşturulması desteklenmez.</br> Kaynak sözlüğü Özelliği değiştiriliyor `Source` .|
|Uygulama çalışırken projenize yeni denetimler, sınıflar, pencereler veya diğer dosyalar ekleme|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|NuGet paketlerini yönetme (paket ekleme/kaldırma/güncelleştirme)|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|{X:Bind} biçimlendirme uzantısını kullanan veri bağlamasını değiştirme|Yok|Visual Studio 2019 ' den itibaren desteklenir|bunun için Windows 10 sürüm 1809 (derleme 10.0.17763) gerekir. Visual Studio 2017 veya önceki sürümlerde desteklenmez.|
|X:Uid yönergelerinin değiştirilmesi desteklenmiyor|Yok|Desteklenmiyor|Hiçbiri|
|Birden çok işlem | Desteklenir | Desteklenir | Visual Studio 2019 [sürüm 16,6](/visualstudio/releases/2019/release-notes-v16.6) ve üzeri sürümlerde desteklenir |

## <a name="error-messages"></a>Hata iletileri

XAML sık yükleme 'yi kullanırken aşağıdaki hatalarda gelebiliriz.

|Hata iletisi|Açıklama|
|-|-|
|Olayın başarısız olduğundan emin olun|Hata, sizin uygulamanız çalışırken desteklenmeyen denetimlerinizin birine bir olay gönderilmeye çalıştığınız anlamına gelir.|
|Bu değişiklik XAML Hot Reload tarafından desteklenmiyor ve hata ayıklama oturumu sırasında uygulanmayacak.|Hata, denediğiniz değişikliğin XAML etkin yeniden yükleme tarafından desteklenmediğini gösterir. Hata ayıklama oturumunu durdurun, değişikliği yapın ve hata ayıklama oturumunu yeniden başlatın. desteklendiğini görmek istediğiniz desteklenmeyen bir senaryo bulursanız, [Visual Studio geliştirici Community](https://aka.ms/feedback/suggest?space=8)yeni "özellik öner" seçeneğini kullanın. |

## <a name="see-also"></a>Ayrıca bkz.

* [XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme](xaml-hot-reload-troubleshooting.md)
* [Xamarin.Forms için XAML Çalışırken Yeniden Yükleme](/xamarin/xamarin-forms/xaml/hot-reload)
* [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

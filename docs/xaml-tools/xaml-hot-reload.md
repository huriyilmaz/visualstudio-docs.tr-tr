---
title: XAML kullanarak XAML kodu yazma ve hata ayıklama XAML kodu yükleme
description: XAML çalışırken yeniden yükleme veya XAML düzenleme ve devam etme, uygulamaları çalıştırırken XAML kodunuzda değişiklik yapmanıza olanak sağlar
ms.date: 10/26/2021
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
ms.openlocfilehash: 5bd1b7c07d4a467c886b2846b8504d8c47f87684
ms.sourcegitcommit: 7a820b7698a8dcf076eb36e3d766fb0751f56bb1
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/02/2021
ms.locfileid: "131128020"
---
# <a name="xaml-hot-reload-write-and-debug-your-wpf-and-uwp-apps-while-theyre-running"></a>XAML Hot Reload: çalışırken WPF ve UWP uygulamalarınızı yazma ve hatalarını ayıklama

XAML Hot Reload ile, çalışan uygulamanın veri bağlamı, kimlik doğrulama durumu ve tasarım zamanı için benzetim yapmak zor olan diğer gerçek karmaşıklığın avantajıyla XAML kodu artımlı olarak oluşturup test edebilirsiniz.

> [!TIP]
> Buraya XAML etkin yeniden yükleme kullanıcı arabirimi (UI) yoluyla ulaşdıysanız, hoş geldiniz! XAML sık yükleme hakkında daha fazla bilgi edinmek için doğru yerdir. Ancak XAML dinamik yeniden yükleme sorunlarını gidermek için yardıma ihtiyacınız varsa bkz. bunun yerine [xaml etkin yeniden yükleme sorunlarını giderme](xaml-hot-reload-troubleshooting.md) .

hem Visual Studio hem de Visual Studio için Blend kullanılabilir, XAML etkin yeniden yükleme özellikle bu senaryolarda yararlı olur:

* Uygulama hata ayıklama modunda başlatıldıktan sonra XAML kodunuzda bulunan Kullanıcı arabirimi sorunlarını düzeltme.

* Uygulamanın çalışma zamanı bağlamından yararlanarak geliştirme aşamasındaki bir uygulama için yeni bir kullanıcı arabirimi bileşeni oluşturma.

|Desteklenen uygulama türleri|İşletim sistemi ve araçlar|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 + ve .net Core</br>Windows 7 ve üzeri |
|evrensel Windows uygulamaları (UWP)| [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + ve üzeri ile Windows 10 ve üzeri|

> [!NOTE]
> Xamarin. Forms kullanıyorsanız, bkz. [Xamarin. Forms Için xaml etkin yeniden yükleme](/xamarin/xamarin-forms/xaml/hot-reload).

Aşağıdaki animasyon, bazı kaynak kodları açmak için canlı görsel ağaç kullanmanın bir örneğini gösterir ve ardından bir düğmenin metin ve rengini değiştirmek için XAML etkin yeniden yükleme ' yi kullanmaktır.

:::image type="content" source="../debugger/media/xaml-hot-reload-using.gif" alt-text="Kaynak kodu açan canlı görsel ağaç animasyonu ve Kullanıcı arabirimi öğelerini değiştirmek için XAML Hot Reload kullanma.":::

> [!NOTE]
> Visual Studio XAML etkin yeniden yüklemesi şu anda yalnızca Visual Studio ' de bir uygulama çalıştırdığınız veya hata ayıklayıcı ekli olan Visual Studio için Blend (**F5** ya da **hata ayıklamayı başlatma**) destekleniyor. [Bir ortam değişkenini el ile](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process)ayarlamadığınız sürece, [İşleme İliştir](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) ' i kullanarak bu deneyimi etkinleştiremezsiniz.

## <a name="known-limitations"></a>Bilinen sınırlamalar

XAML sık yeniden yükleme 'nin bilinen kısıtlamaları aşağıda verilmiştir. ' De çalıştırdığınız herhangi bir sınırlamaya geçici bir çözüm bulmak için, hata ayıklayıcıyı durdurmanız ve sonra işlemi doldurmanız yeterlidir.

|Sınırlama|WPF|UWP|Notlar|
|-|-|-|-|
|Uygulama çalışırken denetimlere yönelik bağlantı olayları|Desteklenmiyor|Desteklenmez|Bkz. hata: *olayın başarısız olduğundan emin olun*. WPF 'de, var olan bir olay işleyicisine başvurabilirsiniz. UWP uygulamalarında, var olan bir olay işleyicisine başvurulması desteklenmez.|
|Uygulamanızın sayfa/pencere veya *app. xaml* gibi bir kaynak sözlüğünde kaynak nesneleri oluşturma|Visual Studio 2019 [sürüm 16,2](/visualstudio/releases/2019/release-notes-v16.2) ve üzeri sürümlerde başlatılıyor|Destekleniyor|Örnekler: <br>- `SolidColorBrush` Olarak kullanmak için bir kaynak sözlüğüne ekleme `StaticResource` .</br>Note: statik kaynaklar, stil dönüştürücüler ve bir kaynak sözlüğüne yazılan diğer öğeler XAML etkin yeniden yükleme kullanılırken uygulanabilir/kullanılabilir. Yalnızca kaynağın oluşturulması desteklenmez.</br> -Kaynak sözlüğü Özelliği değiştiriliyor `Source` .|
|Uygulama çalışırken projenize yeni denetimler, sınıflar, pencereler veya diğer dosyalar ekleme|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|NuGet paketlerini yönetme (paket ekleme/kaldırma/güncelleştirme)|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|{X:Bind} biçimlendirme uzantısını kullanan veri bağlamasını değiştirme|Yok|Visual Studio 2019 ' den itibaren desteklenir|bunun için Windows 10 sürüm 1809 (build 10.0.17763) ve üzeri gerekir. Visual Studio 2017 veya önceki sürümlerde desteklenmez.|
|X:Uid yönergelerinin değiştirilmesi desteklenmiyor|Yok|Desteklenmiyor|Hiçbiri|
|Birden çok işlem kullanma | Desteklenir | Desteklenir | Visual Studio 2019 [sürüm 16,6](/visualstudio/releases/2019/release-notes-v16.6) ve sonraki sürümlerde desteklenir. |

## <a name="error-messages"></a>Hata iletileri

XAML sık yükleme 'yi kullanırken aşağıdaki hatalar arasında gelemeyebilirsiniz.

|Hata iletisi|Description|
|-|-|
|Olayın başarısız olduğundan emin olun|Hata, sizin uygulamanız çalışırken desteklenmeyen denetimlerinizin birine bir olay gönderilmeye çalıştığınız anlamına gelir.|
|Bu değişiklik XAML Hot Reload tarafından desteklenmiyor ve hata ayıklama oturumu sırasında uygulanmayacak.|Hata, denediğiniz değişikliğin XAML etkin yeniden yükleme tarafından desteklenmediğini gösterir. Hata ayıklama oturumunu durdurun, değişikliği yapın ve hata ayıklama oturumunu yeniden başlatın.  |

Desteklendiğini görmek istediğiniz desteklenmeyen bir senaryo bulursanız [bir özellik önerme](../ide/suggest-a-feature.md) seçeneğini kullanarak bize bilgi verin.

## <a name="see-also"></a>Ayrıca bkz.

* [XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme](xaml-hot-reload-troubleshooting.md)
* [Xamarin.Forms için XAML Çalışırken Yeniden Yükleme](/xamarin/xamarin-forms/xaml/hot-reload)
* [Düzenle ve Devam Et (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)

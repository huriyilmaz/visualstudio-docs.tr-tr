---
title: XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme
description: XAML etkin yeniden yükleme ile karşılaşabileceğiniz sorunları giderin.
ms.date: 12/10/2021
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-xaml-tools
ms.workload:
- multiple
ms.openlocfilehash: d4ac862c77e77d17bf77992fb30530e85ad3c57e
ms.sourcegitcommit: 64d6c5cf93984bbb22812577af17128cd2239f79
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/08/2021
ms.locfileid: "134366845"
---
# <a name="troubleshooting-xaml-hot-reload"></a>XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme

Bu sorun giderme kılavuzu, XAML sık yeniden yükleme 'nin düzgün çalışmasını engelleyen çoğu sorunu çözmesi için ayrıntılı yönergeler içerir.

WPF ve UWP uygulamaları için XAML Hot Reload desteklenir. İşletim sistemi ve araç gereksinimleri hakkında daha fazla bilgi için bkz. xaml üzerinde [çalışan XAML kodu yazma ve hata ayıklama xaml çalışırken yeniden yükleme](xaml-hot-reload.md).

## <a name="if-hot-reload-is-not-available"></a>Etkin yeniden yükleme kullanılamıyorsa

Uygulamanızda hata ayıklarken uygulama içi araç çubuğunda "etkin yeniden yükleme kullanılamıyor" iletisini görürseniz, sorunu çözmek için bu makalede açıklanan yönergeleri izleyin.

### <a name="verify-that-xaml-hot-reload-is-enabled"></a>XAML etkin yeniden yükleme özelliğinin etkinleştirildiğini doğrulama

Özelliği varsayılan olarak etkindir. Uygulamanızda hata ayıklamayı başlattığınızda, XAML etkin yeniden yükleme 'nin kullanılabildiğini doğrulayan uygulama içi araç çubuğunu gördiğinizden emin olun:

![XAML etkin yeniden yükleme kullanılabilir](../debugger/media/xaml-hot-reload-available.png)

Uygulama içi araç çubuğunu görmüyorsanız, genel **hata ayıklama**  >  **seçenekleri**' ni açın  >  . Her iki seçenek **için de xaml IÇIN UI hata ayıklama araçları 'Nı etkinleştirin** ve **xaml etkin yeniden yükleme özelliğini etkinleştirin** .

![Visual Studio hata ayıklama seçenekleri penceresinin ekran görüntüsü. Genel hata ayıklama seçenekleri seçilidir ve XAML etkin yeniden yüklemeyi etkinleştir seçeneği işaretlenir.](../debugger/media/xaml-hot-reload-enable.png)

bu seçenekler işaretliyse, canlı görsel ağaç (**hata ayıkla**  >  **Windows**  >  **canlı görsel ağaç**) öğesine gidin ve **çalışma zamanı araçlarını uygulama** araç çubuğunda göster düğmesinin (en solda) seçili olduğundan emin olun.

![Canlı görsel ağaç penceresinin en üstündeki araç çubuğunun, ' uygulama içinde çalışma zamanı araçlarını göster ' düğmesi seçili olan ekran görüntüsü.](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

### <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Işleme eklemek yerine başlatma hata ayıklamayı kullandığınızı doğrulayın

XAML etkin yeniden yükleme, `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` uygulamanın başladığı zaman ortam değişkeninin 1 olarak ayarlanmasını gerektirir. Visual Studio **hata ayıklama**  >  **başlatma hata ayıklama** (veya **F5**) komutunun bir parçası olarak bunu otomatik olarak ayarlar. Bunun yerine, işlemek için **Hata Ayıkla** komutuyla xaml etkin yeniden yükleme kullanmak istiyorsanız  >   , ortam değişkenini kendiniz ayarlayın.

> [!NOTE]
> Bir ortam değişkeni ayarlamak için, Başlat düğmesini kullanarak "ortam değişkeni" araması yapın ve **sistem ortam değişkenlerini Düzenle**' yi seçin. Açılan iletişim kutusunda, **ortam değişkenleri**' ni seçin, sonra bir kullanıcı değişkeni olarak ekleyin ve değerini olarak ayarlayın `1` . Temizlemek için, hata ayıklamayı bitirdiğinizde değişkeni kaldırın.

### <a name="verify-that-your-msbuild-properties-are-correct"></a>MSBuild özelliklerinin doğru olduğundan emin olun

Varsayılan olarak, kaynak bilgisi bir hata ayıklama yapılandırmasına dahildir. proje dosyalarınızda (*. csproj gibi) MSBuild özellikleriyle denetlenir. WPF için, özelliği `XamlDebuggingInformation` olarak ayarlanması gerekir `True` . UWP için, özelliği `DisableXbfLineInfo` olarak ayarlanması gerekir `False` . Örnek:

WPF

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

### <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Doğru derleme yapılandırma adını kullandığınızı doğrulayın

XAML Hot Reload 'i desteklemek için doğru MSBuild özelliğini el ile ayarlamanız gerekir (önceki bölüme bakın) ya da varsayılan derleme yapılandırma adını (hata ayıklama) kullanmanız gerekir. MSBuild özelliğini doğru ayarlamazsanız, özel bir yapı yapılandırma adı çalışmaz veya bir yayın derlemesi olur.

### <a name="verify-that-your-xaml-file-has-no-errors"></a>XAML dosyanızda hata olmadığından emin olun

XAML dosyanız **hata listesi** hatalar gösteriyorsa, daha sonra XAML Hot Reload çalışmayabilir.


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
|Olayın başarısız olduğundan emin olun|Hata, sizin uygulamanızın çalışırken desteklenmeyen denetimlerinizin birine bir olay ile bağlantı kurmaya çalıştığın olduğunu gösterir.|
|Bu değişiklik XAML Hot Reload tarafından desteklenmez ve hata ayıklama oturumu sırasında uygulanmaz.|Hata, denediğiniz değişikliğin XAML etkin yeniden yükleme tarafından desteklenmediğini gösterir. Hata ayıklama oturumunu durdurun, değişikliği yapın ve hata ayıklama oturumunu yeniden başlatın.  |

Desteklendiğini görmek istediğiniz desteklenmeyen bir senaryo bulursanız [bir özellik önerme](../ide/suggest-a-feature.md) seçeneğini kullanarak bize bilgi verin.


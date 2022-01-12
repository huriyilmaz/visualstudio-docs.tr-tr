---
title: XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme
description: Hatalarla karşılaşan sorunları XAML Çalışırken Yeniden Yükleme.
ms.date: 12/17/2021
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
monikerRange: '>=vs-2019'
ms.openlocfilehash: 9beb77799ad45300f582f53e901b777d8aa5cb0e
ms.sourcegitcommit: d3578c384959f1b76dd06fb4b5d075fb052f8c69
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/18/2021
ms.locfileid: "135374896"
---
# <a name="troubleshooting-xaml-hot-reload"></a>XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme

Bu sorun giderme kılavuzu, sorunların çoğunun düzgün bir şekilde XAML Çalışırken Yeniden Yükleme ayrıntılı yönergeler içerir.

XAML Çalışırken Yeniden Yükleme WPF ve UWP uygulamaları için de kullanılabilir. İşletim sistemi ve araç gereksinimleri hakkında ayrıntılı bilgi için [bkz. XAML](xaml-hot-reload.md)kodunu XAML Çalışırken Yeniden Yükleme.

## <a name="if-hot-reload-is-not-available"></a>Çalışırken Yeniden Yükleme kullanılamıyorsa

Uygulamanın hata ayıklaması sırasında Çalışırken Yeniden Yükleme araç çubuğunda "uygulama kullanılamıyor" iletisiyle karşılaşıyorsanız, sorunu çözmek için bu makalede açıklanan yönergeleri izleyin.

### <a name="verify-that-xaml-hot-reload-is-enabled"></a>Uygulamanın XAML Çalışırken Yeniden Yükleme doğrulayın

::: moniker range="vs-2019"

Bu özellik, Visual Studio 2019 ve sonraki sürümlerde varsayılan olarak etkindir. Uygulamanıza hata ayıklamaya başlarken uygulamanın kullanılabilir olduğunu onaylayan uygulama içinde araç XAML Çalışırken Yeniden Yükleme olun:

![Visual Studio 2019'da 'XAML Çalışırken Yeniden Yükleme kullanılabilir' araç çubuğunun ekran görüntüsü](../debugger/media/xaml-hot-reload-available.png)

::: moniker-end

::: moniker range="vs-2022"

Bu özellik 2022 ve Visual Studio varsayılan olarak etkindir. Uygulamanıza hata ayıklamaya başlarken uygulamanın kullanılabilir olduğunu onaylayan uygulama içinde araç XAML Çalışırken Yeniden Yükleme olun:

![Visual Studio 2022'de 'XAML Çalışırken Yeniden Yükleme kullanılabilir' araç çubuğunun ekran görüntüsü](../debugger/media/vs-2022/xaml-hot-reload-available.png)

::: moniker-end

Uygulama içinde araç çubuğunu görmüyorsanız, uygulamanın menü çubuğundan   >    >  **XAML Çalışırken Yeniden Yükleme** Ayıklama Seçenekleri'Visual Studio seçin. Ardından, Seçenekler **iletişim** kutusunda, Etkinleştir seçeneğinin **XAML Çalışırken Yeniden Yükleme** emin olun.

![Hata Ayıklama Visual Studio penceresinin ekran görüntüsü, Etkinleştir seçeneği XAML Çalışırken Yeniden Yükleme vurgulanmış.](../debugger/media/vs-2022/xaml-hot-reload-enable.png)

### <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>İşleme Ekleme yerine Hata Ayıklamayı Başlat'ı kullanmakta olduğunu doğrulayın

XAML Çalışırken Yeniden Yükleme, uygulama başlatıldığında ortam `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` değişkeninin 1 olarak ayarlanmıştır. Visual Studio Hata AyıklamaYı Başlat   >  (veya **F5**)**komutunun** bir parçası olarak bunu otomatik olarak ayarlar. Bunun yerine hata ayıklama XAML Çalışırken Yeniden Yükleme komutuyla birlikte kullanmak için ortam değişkenlerini kendiniz  >   ayarlayın.

> [!NOTE]
> Ortam değişkeni ayarlamak için Başlat düğmesini kullanarak "ortam değişkeni" araması yapmak ve Sistem ortam **değişkenlerini düzenle'yi seçin.** Açılan iletişim kutusunda Ortam **Değişkenleri'ne tıklayın,** ardından bunu bir kullanıcı değişkeni olarak ekleyin ve değerini olarak `1` ayarlayın. Temizlemek için, hata ayıklamayı bitirdikten sonra değişkenlerini kaldırın.

### <a name="verify-that-your-msbuild-properties-are-correct"></a>Uygulama özelliklerinizin MSBuild doğrulayın

Varsayılan olarak, kaynak bilgileri hata ayıklama yapılandırmasına dahil edilir. Proje dosyalarınıza MSBuild özellikleriyle denetlenmiştir (*.csproj gibi). WPF için özelliği `XamlDebuggingInformation` değeridir ve bu değeri olarak ayarlandır. `True` UWP için özelliği `DisableXbfLineInfo` değeridir ve bu değeri olarak ayarlandır. `False` Örneğin:

WPF:

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP:

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

### <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Doğru derleme yapılandırma adını kullanmakta olduğunu doğrulayın

Bu özelliği desteklemek için doğru MSBuild özelliğini el ile XAML Çalışırken Yeniden Yükleme (önceki bölüme bakın) veya varsayılan derleme yapılandırma adını (Hata Ayıklama) kullanmalısınız. MSBuild özelliğini doğru ayarlayamasanız, özel bir derleme yapılandırma adı çalışmaz ve yayın derlemesi de çalışmaz.

### <a name="verify-that-your-xaml-file-has-no-errors"></a>XAML dosyanız için hata olmadığını doğrulayın

XAML dosyanız Hata Listesinde hatalar **gösteriyorsa,** XAML Çalışırken Yeniden Yükleme çalışmayabilirsiniz.

## <a name="known-limitations"></a>Bilinen sınırlamalar

Aşağıdakiler, bilinen XAML Çalışırken Yeniden Yükleme. Karşılaşacak herhangi bir sınırlamaya çözüm olarak hata ayıklayıcıyı durdurmanız ve ardından işlemi tamamlamanız gerekir.

|Sınırlama|WPF|UWP|Notlar|
|-|-|-|-|
|Uygulama çalışırken olayları denetimlere kablolama|Desteklenmiyor|Desteklenmez|Hataya bakın: *Olayın Başarısız Olduğundan Emin Oldu.* WPF'de, mevcut bir olay işleyiciye başvurabilirsiniz. UWP uygulamaları için mevcut olay işleyiciye başvuru desteklenmiyor.|
|Kaynak sözlüğünde, uygulamanın Sayfa/Pencere veya *App.xaml'sinde* bulunanlar gibi kaynak nesneleri oluşturma|Visual Studio 2019 sürüm [16.2](/visualstudio/releases/2019/release-notes-v16.2) ve sonraki sürümlerde başlayan destek|Desteklenir|Örnekler: <br>- Kaynak `SolidColorBrush` sözlüğüne olarak kullanmak üzere bir `StaticResource` ekleme.</br>Not: Statik kaynaklar, stil dönüştürücüler ve kaynak sözlüğüne yazılan diğer öğeler, kaynak sözlüğünü kullanırken uygulanabilir/XAML Çalışırken Yeniden Yükleme. Yalnızca kaynağın oluşturulması desteklenmiyor.</br> - Kaynak sözlüğü özelliğini `Source` değiştirme.|
|Uygulama çalışırken projenize yeni denetimler, sınıflar, pencereler veya diğer dosyalar ekleme|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|Paket NuGet yönetme (paket ekleme/kaldırma/güncelleştirme)|Desteklenmiyor|Desteklenmiyor|Hiçbiri|
|{x:Bind} işaretleme uzantısını kullanan veri bağlamayı değiştirme|Yok|Visual Studio 2019'dan itibaren destek|Bunun için Windows 10 1809 (derleme 10.0.17763) ve sonraki bir sürümü gerekir. 2017 Visual Studio önceki sürümlerde desteklenmiyor.|
|x:Uid yönergelerini değiştirme desteklenmiyor|Yok|Desteklenmiyor|Hiçbiri|
|Birden çok işlem kullanma | Desteklenir | Desteklenir | Visual Studio 2019 [sürüm 16.6 ve sonraki sürümlerde](/visualstudio/releases/2019/release-notes-v16.6) de destekleni. |

## <a name="error-messages"></a>Hata iletileri

Uygulama kullanırken aşağıdaki hatalara XAML Çalışırken Yeniden Yükleme.

|Hata iletisi|Description|
|-|-|
|Olayın Başarısız Olduğundan Emin Olmak|Hata, bir olayı denetimlerinden biri ile bağlantıya çalıştığınıza işaret ediyor ve bu durum uygulama çalışırken desteklenmiyor.|
|Bu değişiklik uygulama tarafından XAML Çalışırken Yeniden Yükleme ve hata ayıklama oturumu sırasında uygulanmaz.|Hata, çalıştığınız değişikliğin uygulama tarafından desteklene XAML Çalışırken Yeniden Yükleme. Hata ayıklama oturumunu durdurun, değişikliğin ardından hata ayıklama oturumunu yeniden başlatın.  |

Destekleneni görmek istediğiniz desteklenmeyen bir senaryo bulursanız Özellik önerin seçeneğini kullanarak [bize haber](../ide/suggest-a-feature.md) verin.
---
title: XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme
description: XAML etkin yeniden yükleme ile karşılaşabileceğiniz sorunları giderin.
ms.date: 09/04/2019
ms.topic: troubleshooting
helpviewer_keywords:
- xaml edit and continue, troubleshooting
- xaml hot reload, troubleshooting
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 73d8653b2bcf06801c18e21d9a13b21843abc7d7
ms.sourcegitcommit: 9de7d25056da59df0941508c80c0b12766ba6580
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/27/2020
ms.locfileid: "77706380"
---
# <a name="troubleshooting-xaml-hot-reload"></a>XAML Çalışırken Yeniden Yükleme ile ilgili sorunları giderme

Bu sorun giderme kılavuzu, XAML sık yeniden yükleme 'nin düzgün çalışmasını engelleyen çoğu sorunu çözmesi için ayrıntılı yönergeler içerir.

WPF ve UWP uygulamaları için XAML Hot Reload desteklenir. İşletim sistemi ve araç gereksinimleri hakkında daha fazla bilgi için bkz. xaml üzerinde [çalışan XAML kodu yazma ve hata ayıklama xaml çalışırken yeniden yükleme](xaml-hot-reload.md).

## <a name="hot-reload-is-not-available"></a>Sık yeniden yükleme kullanılamıyor

Uygulamanızda hata ayıklarken uygulama içi araç çubuğunda "etkin yeniden yükleme kullanılamıyor" iletisini görürseniz, sorunu çözmek için bu makalede açıklanan yönergeleri izleyin.

## <a name="verify-that-xaml-hot-reload-is-enabled"></a>XAML etkin yeniden yükleme özelliğinin etkinleştirildiğini doğrulama

Özelliği varsayılan olarak etkindir. Uygulamanızda hata ayıklamayı başlattığınızda, XAML etkin yeniden yükleme 'nin kullanılabildiğini doğrulayan uygulama içi araç çubuğunu gördiğinizden emin olun:

![XAML etkin yeniden yükleme kullanılabilir](../debugger/media/xaml-hot-reload-available.png)

Uygulama içi araç çubuğunu görmüyorsanız, **genel** > **hata ayıklama** > **seçeneklerini** açın. Her iki seçenek **için de xaml IÇIN UI hata ayıklama araçları 'Nı etkinleştirin** ve **xaml etkin yeniden yükleme özelliğini etkinleştirin** .

![XAML etkin yeniden yüklemeyi etkinleştir](../debugger/media/xaml-hot-reload-enable.png)

Bu seçenekler işaretliyse, canlı görsel ağaç (**hata ayıkla** > **Windows** > **canlı görsel ağaç**) öğesine gidin ve **çalışma zamanı araçlarının uygulama** araç çubuğunda (en solda) seçili olduğundan emin olun.

![XAML etkin yeniden yüklemeyi etkinleştir](../debugger/media/xaml-hot-reload-show-runtime-tools.png)

## <a name="verify-that-you-use-start-debugging-rather-than-attach-to-process"></a>Işleme eklemek yerine başlatma hata ayıklamayı kullandığınızı doğrulayın

XAML etkin yeniden yükleme, uygulamanın başladığı zaman `ENABLE_XAML_DIAGNOSTICS_SOURCE_INFO` ortam değişkeninin 1 olarak ayarlanmasını gerektirir. Visual Studio bunu, **hata** **ayıklamayı Başlat** (veya **F5**) komutunun bir parçası olarak otomatik olarak ayarlar > . Bunun yerine, **hata ayıkla** > **Işleme Ekle** komutuyla xaml etkin yeniden yükleme kullanmak istiyorsanız, ortam değişkenini kendiniz ayarlayın.

> [!NOTE]
> Bir ortam değişkeni ayarlamak için, Başlat düğmesini kullanarak "ortam değişkeni" araması yapın ve **sistem ortam değişkenlerini Düzenle**' yi seçin. Açılan iletişim kutusunda, **ortam değişkenleri**' ni seçin, sonra bir kullanıcı değişkeni olarak ekleyin ve değeri `1`olarak ayarlayın. Temizlemek için, hata ayıklamayı bitirdiğinizde değişkeni kaldırın.

## <a name="verify-that-your-msbuild-properties-are-correct"></a>MSBuild özelliklerinin doğru olduğundan emin olun

Varsayılan olarak, kaynak bilgisi bir hata ayıklama yapılandırmasına dahildir. Proje dosyalarınızda MSBuild özellikleri (*. csproj gibi) tarafından denetlenir. WPF için, özelliği, `True`olarak ayarlanması gereken `XamlDebuggingInformation`. UWP için, özelliği, `False`olarak ayarlanması gereken `DisableXbfLineInfo`. Örnek:

WPF

`<XamlDebuggingInformation>True</XamlDebuggingInformation>`

UWP

`<DisableXbfLineInfo>False</DisableXbfLineInfo>`

## <a name="verify-that-you-are-using-the-correct-build-configuration-name"></a>Doğru derleme yapılandırma adını kullandığınızı doğrulayın

XAML Hot Reload 'i desteklemek için doğru MSBuild özelliğini el ile ayarlamanız gerekir (önceki bölüme bakın) ya da varsayılan derleme yapılandırma adını (hata ayıklama) kullanmanız gerekir. MSBuild özelliğini doğru ayarlamazsanız, özel bir yapı yapılandırma adı çalışmaz veya bir yayın derlemesi olur.

## <a name="verify-that-your-xaml-file-has-no-errors"></a>XAML dosyanızda hata olmadığından emin olun

XAML dosyanız **hata listesi**hatalar gösteriyorsa, daha sonra XAML Hot Reload çalışmayabilir.

## <a name="see-also"></a>Ayrıca bkz.

[Xaml dinamik yeniden yüklemesine çalışan XAML kodu yazma ve hata ayıklama](xaml-hot-reload.md)

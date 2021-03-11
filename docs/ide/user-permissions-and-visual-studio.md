---
title: Yönetici olarak çalıştır ögesini seçin
description: Visual Studio 'Yu yönetici olarak çalıştırmayı öğrenin.
ms.date: 03/09/2021
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b3d2a22533137bf2c1f2e7cfeb3802f5824c3926
ms.sourcegitcommit: f9ed9c4c6c166ef9826feb21dcb9c4d47ed14e1a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/10/2021
ms.locfileid: "102607255"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı izinleri ve Visual Studio

Güvenlik nedenleriyle, mümkün olan her durumda Visual Studio 'Yu normal bir kullanıcı olarak çalıştırmanız gerekir.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

Normal bir kullanıcı olarak Visual Studio IDE 'deki neredeyse her şeyi yapabilirsiniz. Aşağıdaki görevleri gerçekleştirmek için yönetici izinlerine sahip olmanız gerekir:

|Alan|Görev|Daha fazla bilgi edinmek için|
|----------|----------| - |
|Yükleme|Visual Studio 'Yu yükler veya değiştirir.|[Visual Studio 'Yu yüklemeyi](../install/install-visual-studio.md), [Visual Studio 'yu değiştirme](../install/modify-visual-studio.md)|
||Yerel Yardım içeriğini yükler, güncelleştirir veya kaldırır.|[Yerel Yardım içeriğini yükleyip yönetme](../help-viewer/install-manage-local-content.md)|
|Araç Kutusu|**Araç kutusuna** klasik com denetimleri ekleyin.|[Araç Kutusu](../ide/reference/toolbox.md)|
|Oluşturma|Bir bileşeni kaydeden oluşturma sonrası olayları kullanın.|[Özel derleme adımlarını ve derleme olaylarını anlama](/cpp/build/understanding-custom-build-steps-and-build-events)|
||C++ projeleri oluşturduğunuzda bir kayıt adımı ekleyin.||
|Hata Ayıklama|Yükseltilmiş izinlerle çalışan uygulamalarda hata ayıklayın.|[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET Web siteleri gibi farklı bir kullanıcı hesabı altında çalışan uygulamalarda hata ayıklayın.|[ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XAML tarayıcı uygulamaları (XBAP) için bölgede hata ayıklama.|[WPF konağı (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Microsoft Azure için bulut hizmeti projelerinde hata ayıklamak için öykünücüyü kullanın.|[Visual Studio 'da bir bulut hizmetinde hata ayıklama](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Uzaktan hata ayıklama için bir güvenlik duvarı yapılandırın.|[Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Performans araçları|Yükseltilmiş bir uygulamaya iliştirme.|[Performans profili oluşturma için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
||GPU Profiler 'ı kullanın.|[GPU profili oluşturma](../profiling/gpu-usage.md)|
|Dağıtım|Bir Web uygulamasını yerel bir bilgisayarda Internet Information Services (IIS) uygulamasına dağıtın.|[Visual Studio kullanarak bir ASP.NET Web uygulaması dağıtma](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio 'Yu yönetici olarak çalıştırma

Visual Studio 'Yu yönetici olarak çalıştırmanız gerekiyorsa IDE 'yi açmak için aşağıdaki adımları izleyin:

> [!NOTE]
> Bu yönergeler Windows 10 içindir. Bunlar, diğer Windows sürümlerine benzerdir.

::: moniker range="vs-2017"

1. **Başlat** menüsünü açın ve Visual Studio 2017 ' a kaydırın.

1. **Visual Studio 2017**' nin sağ tıklama veya bağlam menüsünden **daha fazla** > **Çalıştır yönetici**' yi seçin.

   Visual Studio başladığında, başlık çubuğunda ürün adından sonra **(yönetici)** görüntülenir.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Başlat** menüsünü açın ve Visual Studio 2019 ' a kaydırın.

1. **Visual Studio 2019**' nin sağ tıklama veya bağlam menüsünden **daha fazla** > **Çalıştır yönetici**' yi seçin.

   Visual Studio başladığında, başlık çubuğunda ürün adından sonra **(yönetici)** görüntülenir.

::: moniker-end

Ayrıca, uygulama kısayolunu her zaman yönetici izinleriyle çalışacak şekilde değiştirebilirsiniz:

1. **Başlat** menüsünü açın, kullandığınız Visual Studio sürümüne kaydırın ve **daha fazla**  >  **Açık dosya konumu**' nu seçin.

1. **Dosya Gezgini**'nde, kullanmakta olduğunuz sürüm Için **Visual Studio** kısayolunu bulun. Ardından, kısayolu sağ tıklatın ve masaüstüne **Gönder**  >  **(kısayol oluştur)** seçeneğini belirleyin.

1. **Windows** masaüstünde, **Visual Studio** kısayoluna sağ tıklayın ve ardından **Özellikler**' i seçin.

1. **Gelişmiş** düğmesini seçin ve ardından **yönetici olarak çalıştır** onay kutusunu seçin.

1. **Tamam**’ı ve ardından tekrar **Tamam**’ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio'yu yükleme](../install/install-visual-studio.md)

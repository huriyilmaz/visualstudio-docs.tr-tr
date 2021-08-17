---
title: Yönetici olarak çalıştır ögesini seçin
description: Visual Studio yönetici olarak çalıştırmayı öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 03338da39eb9be3d080839c4c0cd567e3162da7e871bb449f08242c49eed6f5a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121386621"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı izinleri ve Visual Studio

güvenlik nedenleriyle, mümkün olan her durumda Visual Studio tipik bir kullanıcı olarak çalıştırmalısınız.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

Visual Studio ıde 'deki neredeyse her şeyi tipik bir kullanıcı olarak yapabilirsiniz. Aşağıdaki görevleri gerçekleştirmek için yönetici izinlerine sahip olmanız gerekir:

|Alan|Görev|Daha fazla bilgi edinmek için|
|----------|----------| - |
|Yükleme|Visual Studio yükleyip değiştirin.|[Visual Studio yükleyip](../install/install-visual-studio.md) [değiştirme Visual Studio](../install/modify-visual-studio.md)|
||Yerel Yardım içeriğini yükler, güncelleştirir veya kaldırır.|[Yerel Yardım içeriğini yükleyip yönetme](../help-viewer/install-manage-local-content.md)|
|Araç Kutusu|**Araç kutusuna** klasik com denetimleri ekleyin.|[Araç Kutusu](../ide/reference/toolbox.md)|
|Oluşturma|Bir bileşeni kaydeden oluşturma sonrası olayları kullanın.|[Özel derleme adımlarını ve derleme olaylarını anlama](/cpp/build/understanding-custom-build-steps-and-build-events)|
||C++ projeleri oluşturduğunuzda bir kayıt adımı ekleyin.||
|Hata Ayıklama|Yükseltilmiş izinlerle çalışan uygulamalarda hata ayıklayın.|[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET web siteleri gibi farklı bir kullanıcı hesabı altında çalışan uygulamalarda hata ayıklayın.|[ASP.NET ve AJAX uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XAML tarayıcı uygulamaları (XBAP) için bölgede hata ayıklama.|[WPF konağı (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Microsoft Azure için bulut hizmeti projelerinde hata ayıklamak için öykünücüyü kullanın.|[Visual Studio bir bulut hizmetinde hata ayıklama](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Uzaktan hata ayıklama için bir güvenlik duvarı yapılandırın.|[Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Performans araçları|Yükseltilmiş bir uygulamaya iliştirme.|[Performans profili oluşturma için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
||GPU Profiler 'ı kullanın.|[GPU profili oluşturma](../profiling/gpu-usage.md)|
|Dağıtım|bir web uygulamasını yerel bir bilgisayarda Internet Information Services (ııs) uygulamasına dağıtın.|[Visual Studio kullanarak ASP.NET web uygulaması dağıtma](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio yönetici olarak çalıştırma

Visual Studio yönetici olarak çalıştırmanız gerekiyorsa, ıde 'yi açmak için aşağıdaki adımları izleyin:

> [!NOTE]
> Bu yönergeler Windows 10 içindir. Diğer Windows sürümlerine benzerdir.

::: moniker range="vs-2017"

1. **başlat** menüsünü açın ve Visual Studio 2017 ' ye kaydırın.

1. **Visual Studio 2017**' nin sağ tıklama veya bağlam menüsünden **daha fazla** > **çalıştır yönetici**' yi seçin.

   Visual Studio başladığında, **(yönetici)** başlık çubuğundaki ürün adından sonra görüntülenir.

::: moniker-end

::: moniker range=">=vs-2019"

1. **başlat** menüsünü açın ve Visual Studio 2019 ' ye kaydırın.

1. **Visual Studio 2019**' nin sağ tıklama veya bağlam menüsünden **daha fazla** > **çalıştır yönetici**' yi seçin.

   Visual Studio başladığında, **(yönetici)** başlık çubuğundaki ürün adından sonra görüntülenir.

::: moniker-end

Ayrıca, uygulama kısayolunu her zaman yönetici izinleriyle çalışacak şekilde değiştirebilirsiniz:

1. **başlat** menüsünü açın, kullanmakta olduğunuz Visual Studio sürümüne kaydırın ve **daha sonra daha fazla**  >  **açık dosya konumu** seçin.

1. **dosya gezgini**'nde, kullanmakta olduğunuz sürümün **Visual Studio** kısayolunu bulun. Ardından, kısayolu sağ tıklatın ve masaüstüne **Gönder**  >  **(kısayol oluştur)** seçeneğini belirleyin.

1. **Windows** masaüstünde, **Visual Studio** kısayoluna sağ tıklayın ve ardından **özellikler**' i seçin.

1. **Gelişmiş** düğmesini seçin ve ardından **yönetici olarak çalıştır** onay kutusunu seçin.

1. **Tamam**’ı ve ardından tekrar **Tamam**’ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio'yu yükleme](../install/install-visual-studio.md)

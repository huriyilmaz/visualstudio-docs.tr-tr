---
title: Yönetici olarak çalıştır ögesini seçin
ms.date: 01/06/2020
ms.topic: conceptual
helpviewer_keywords:
- Visual Studio, user permissions
- user permissions
- administrative privileges
- permissions
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 927031b4755644aeac553367a4f8a08faa0c0992
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75718642"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı izinleri ve Visual Studio

Güvenlik nedeniyle, Visual Studio'u mümkün olduğunca tipik bir kullanıcı olarak çalıştırmalısınız.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

Tipik bir kullanıcı olarak Visual Studio IDE'de neredeyse her şeyi yapabilirsiniz. Aşağıdaki görevleri tamamlamak için yönetici izinlerine ihtiyacınız vardır:

|Alan|Görev|Daha fazla bilgi edinmek için|
|----------|----------| - |
|Yükleme|Visual Studio'yı yükleyin veya değiştirin.|[Visual Studio'yı yükleyin,](../install/install-visual-studio.md) [Visual Studio'yı değiştirin](../install/modify-visual-studio.md)|
||Yerel Yardım içeriğini yükleyin, güncelleyin veya kaldırın.|[Yerel Yardım içeriğini yükleme ve yönetme](../help-viewer/install-manage-local-content.md)|
|Araç Kutusu|**Toolbox'a**klasik COM denetimleri ekleyin.|[Araç Kutusu](../ide/reference/toolbox.md)|
|Oluşturma|Bir bileşeni kaydeden yapı sonrası olayları kullanın.|[Özel yapı adımlarını anlama ve olayları oluşturma](/cpp/build/understanding-custom-build-steps-and-build-events)|
||C++ projeleri oluştururken bir kayıt adımı ekleyin.||
|Hata ayıklama|Yüksek izinlerle çalışan hata ayıklama uygulamaları.|[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||ASP.NET web siteleri gibi farklı bir kullanıcı hesabı altında çalışan hata ayıklama uygulamaları.|[Hata ayıklama ASP.NET ve AJAX uygulamaları](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XAML Tarayıcı Uygulamaları (XBAP) için Bölge Hata Ayıklama.|[WPF ana bilgisayar (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Microsoft Azure için bulut hizmeti projelerini hata ayıklamak için emülatör'ün kullanın.|[Visual Studio'da bulut hizmetini hata ayıklama](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Uzaktan hata ayıklama için bir güvenlik duvarı yapılandırın.|[Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Performans araçları|Yükseltilmiş bir uygulamaya bağlanma.|[Performans profilleme için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
||GPU Profil oluşturucuyu kullanın.|[GPU profil oluşturma](../profiling/gpu-usage.md)|
|Dağıtım|Yerel bir bilgisayarda Internet Information Services'a (IIS) bir web uygulaması dağıtın.|[Visual Studio'yı kullanarak ASP.NET bir web uygulaması dağıtma](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Visual Studio'u yönetici olarak çalıştırın

Visual Studio'yu yönetici olarak çalıştırmanız gerekiyorsa, IDE'yi açmak için aşağıdaki adımları izleyin:

> [!NOTE]
> Bu yönergeler Windows 10 içindir. Bunlar, Windows'un diğer sürümleri için de benzerdir.

::: moniker range="vs-2017"

1. **Başlat** menüsünü açın ve Visual Studio 2017'ye gidin.

1. **Visual Studio 2017'nin**sağ tıklama veya bağlam menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı**seçin.

   Visual Studio başlatıldığında, **(Administrator)** başlık çubuğundaki ürün adından sonra görünür.

::: moniker-end

::: moniker range=">=vs-2019"

1. **Başlat** menüsünü açın ve Visual Studio 2019'a gidin.

1. **Visual Studio 2019'un**sağ tıklama veya bağlam menüsünden yönetici olarak **Daha Fazla** > **Çalıştır'ı**seçin.

   Visual Studio başlatıldığında, **(Administrator)** başlık çubuğundaki ürün adından sonra görünür.

::: moniker-end

Uygulama kısayolu'nu her zaman yönetim izinleriyle çalışacak şekilde de değiştirebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio projelerini port, geçiş ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio yükleme](../install/install-visual-studio.md)

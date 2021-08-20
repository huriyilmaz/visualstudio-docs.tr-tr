---
title: Yönetici olarak çalıştır ögesini seçin
description: Yönetici olarak Visual Studio çalıştırmayı öğrenin.
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
ms.openlocfilehash: 1c0f1aa61371a3caecad6dbc30874db6299a2283
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122061564"
---
# <a name="user-permissions-and-visual-studio"></a>Kullanıcı izinleri ve Visual Studio

Güvenlik nedenleriyle, mümkün olan her Visual Studio tipik bir kullanıcı olarak çalıştırmalısiniz.

> [!WARNING]
> Ayrıca güvenilir bir kişi ya da güvenilir bir konumdan gelmeyen herhangi bir Visual Studio çözümüyle derleme, başlatma veya hata ayıklama yapmadığınızdan emin olmalısınız.

IDE'de normal bir kullanıcı Visual Studio neredeyse her şeyi yapabiliriz. Aşağıdaki görevleri tamamlamak için yönetici izinlerine ihtiyacınız vardır:

|Alan|Görev|Daha fazla bilgi edinmek için|
|----------|----------| - |
|Yükleme|Yükleme veya değiştirme Visual Studio.|[Yükleme Visual Studio,](../install/install-visual-studio.md) [Değiştirme Visual Studio](../install/modify-visual-studio.md)|
||Yerel Yardım içeriğini yükleyin, güncelleştirin veya kaldırın.|[Yerel Yardım içeriğini yükleme ve yönetme](../help-viewer/install-manage-local-content.md)|
|Araç Kutusu|Araç Kutusuna klasik COM **denetimleri ekleyin.**|[Araç Kutusu](../ide/reference/toolbox.md)|
|Oluşturma|Bir bileşeni kaydeden derleme sonrası olayları kullanın.|[Özel derleme adımlarını ve derleme olaylarını anlama](/cpp/build/understanding-custom-build-steps-and-build-events)|
||C++ projeleri derleme sırasında bir kayıt adımı dahil edin.||
|Hata Ayıklama|Yükseltilmiş izinlerle çalıştıran uygulamalarda hata ayıklama.|[Hata ayıklayıcısı ayarları ve hazırlığı](../debugger/debugger-settings-and-preparation.md)|
||Bir kullanıcının web siteleri gibi farklı bir kullanıcı hesabı altında çalıştırarak ASP.NET ayıklar.|[ASP.NET AJAX uygulamalarında hata ayıklama](../debugger/how-to-enable-debugging-for-aspnet-applications.md)|
||XAML Tarayıcı Uygulamaları (XBAP) için Bölgede Hata Ayıklama.|[WPF ana bilgisayarı (PresentationHost.exe)](/dotnet/framework/wpf/app-development/wpf-host-presentationhost-exe)|
||Bulut hizmeti projelerinde hata ayıklamak için öykünücü Microsoft Azure.|[Visual Studio'de bulut hizmetinin hata ayıklaması](/azure/vs-azure-tools-debug-cloud-services-virtual-machines)|
||Uzaktan hata ayıklama için bir güvenlik duvarı yapılandırma.|[Uzaktan hata ayıklama](../debugger/remote-debugging.md)|
|Performans araçları|Yükseltilmiş bir uygulamaya ekleme.|[Performans profili oluşturma için yeni başlayanlar kılavuzu](../profiling/beginners-guide-to-performance-profiling.md)|
||GPU ProfilLeyici'lerini kullanın.|[GPU profili oluşturma](../profiling/gpu-usage.md)|
|Dağıtım|Web uygulamasını yerel bir Internet Information Services (IIS) uygulamasına dağıtın.|[Visual Studio kullanarak ASP.NET web uygulaması Visual Studio](/aspnet/web-forms/overview/older-versions-getting-started/deployment-to-a-hosting-provider/)|

## <a name="run-visual-studio-as-an-administrator"></a>Yönetici Visual Studio olarak çalıştırma

Yönetici olarak bir Visual Studio çalıştırmanız gerekirse, IDE'i açmak için şu adımları izleyin:

> [!NOTE]
> Bu yönergeler, Windows 10. Bunlar, diğer sürümler için Windows.

::: moniker range="vs-2017"

1. Başlat menüsünü **açın** ve 2017'Visual Studio kaydırın.

1. **Visual Studio 2017'nin** sağ tıklama veya bağlam menüsünde Yönetici **olarak** daha fazla > **çalıştır'ı seçin.**

   Yeni Visual Studio başlığı çubuğunda ürün adının ardından **(Yönetici)** görünür.

::: moniker-end

::: moniker range=">=vs-2019"

1. Başlat menüsünü **açın** ve 2019'Visual Studio kaydırın.

1. **Visual Studio 2019'un** sağ tıklayın veya bağlam menüsünde Yönetici **olarak** daha fazla > **çalıştır'ı seçin.**

   Yeni Visual Studio başlığı çubuğunda ürün adının ardından **(Yönetici)** görünür.

::: moniker-end

Uygulama kısayolunu her zaman yönetici izinleriyle çalıştırılacak şekilde de değiştirebilirsiniz:

1. Başlat **menüsünü açın,** kullanmakta Visual Studio sürümüne kaydırın ve Daha Fazla Dosya konumu  >  **aç'ı seçin.**

1. Bu **Dosya Gezgini,** **Visual Studio** sürümü için uygulama kısayolunu bulun. Ardından kısayola sağ tıklayın ve Masaüstüne Gönder  >  **(kısayol oluştur) öğesini seçin.**

1. Masaüstünde **Windows** kısayolunu sağ tıklatın **ve Visual Studio'yi** **seçin.**

1. Gelişmiş **düğmesini** ve ardından Yönetici olarak çalıştır **onay kutusunu** seçin.

1. **Tamam**’ı ve ardından tekrar **Tamam**’ı seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Projeleri taşıma, geçirme ve Visual Studio yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
- [Visual Studio'yu yükleme](../install/install-visual-studio.md)

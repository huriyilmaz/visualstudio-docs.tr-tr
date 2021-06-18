---
title: Visual Studio sürümlerini yan yana yükleme
description: Visual Studio 'nun önceki veya sonraki bir sürümünü Visual Studio 'nun zaten yüklü olduğu bir bilgisayara nasıl yükleyeceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/29/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: j-martens
ms.author: jmartens
manager: jmartens
ms.openlocfilehash: c8d1da5f8cb5c237fe02a41197825d5086fc6471
ms.sourcegitcommit: 5fb4a67a8208707e79dc09601e8db70b16ba7192
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/17/2021
ms.locfileid: "112307027"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme

Visual Studio 'Yu daha önceki veya sonraki bir Visual Studio sürümü yüklü olan bir bilgisayara yükleyebilirsiniz.

::: moniker range="vs-2017"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2015 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2017 kullanıyorsanız, Visual Studio 2017 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra eski sürümde açabilir ve değiştirebilirsiniz.

* Visual Studio 2015 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2017 ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2017 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true) sayfası.

::: moniker-end

::: moniker range="vs-2019"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2017 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2019 kullanıyorsanız, Visual Studio 2019 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra eski sürümde açabilir ve değiştirebilirsiniz.

* Visual Studio 2017 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2019 ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2019 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md) sayfası.

::: moniker-end

::: moniker range=">=vs-2022"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2017 veya Visual Studio 2019 içinde oluşturulmuş bir çözümü açmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022 ' e özgü herhangi bir özelliği uygulamamışsanız daha sonra çözümü daha sonra yeniden açıp değiştirebilirsiniz.

* Visual Studio 2019 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2022 ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2022 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md) sayfası.

::: moniker-end

* Birden fazla sürümünün yüklü olduğu bir bilgisayarda Visual Studio 'nun bir sürümünü kaldırırsanız, Visual Studio için dosya ilişkilendirmeleri tüm sürümler için kaldırılır.

* Tüm uzantılar uyumlu olmadığından, Visual Studio uzantıları otomatik olarak yükseltmez. Uzantıları [Visual Studio Market](https://marketplace.visualstudio.com/) veya yazılım yayımcısından yeniden yüklemeniz gerekir.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>İkincil Visual Studio sürümlerini yan yana yükler

Visual Studio 'nun bir alt sürümünden sonraki bir sürümüne yükseltirken, Visual Studio yükleyicisi varsayılan olarak, geçerli yüklemenizi o kanaldaki en son sürüme güncelleştirmeyecektir. Örneğin, 16.9.4 yeni bir yayın olduğunu varsayalım. Her iki sürüm de [Visual Studio 2019 sürüm kanalının](/visualstudio/productinfo/release-rhythm)bir parçası olduğundan, yükleyici geçerli 16.9.3 (veya daha düşük) yüklemenizi 16.9.4 ile değiştirmeye çalışır. Güncelleştirme sırasında eski sürümü daha yeni sürümle değiştirmek, Visual Studio 'nun eski sürümlerinin makinenizde yer kaplamadığından emin olmanıza yardımcı olur. Ancak bazı belirli durumlarda, Visual Studio 'nun farklı küçük yayın sürümlerini yan yana yüklemek faydalı olabilir. Örneğin, aynı makinede hem 16.9.3 hem de 16.9.4 olmak isteyebilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio 2017 sürüm 15,9 için en son önyükleyici 'yi Visual Studio [önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasından, Visual Studio 'nun mevcut sürümünüzle yan yana yüklemek istediğiniz sürüme indirin.

1. Komut istemi 'ni yönetici modunda açın. Bunu yapmak için, Windows Başlat menüsünü açın, "cmd" yazın, komut Istemi arama sonuçlarına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. Komut isteminde dizinini, Visual Studio önyükleyici dosyanızın bulunduğu klasör olarak değiştirin.

1. Yükleme konumu için yeni bir klasör yolu belirterek ve .exe dosya adını yüklemekte olduğunuz Visual Studio sürümü için uygun önyükleyici adı ile değiştirerek aşağıdaki komutu çalıştırın. .exe dosya adı eşleşmelidir veya aşağıdaki dosyalardan birine benzer olmalıdır:

   * Visual Studio Enterprise için vs_enterprise.exe
   * Visual Studio Professional için vs_professional.exe

1. Yüklemeniz için gereken bileşenleri seçmek üzere Yükleyici iletişim kutularını izleyin. Daha fazla bilgi için bkz. [Visual Studio 'Yu yükler](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 önyükleyici dosyasını Visual Studio [İndirmeleri sayfasından](https://visualstudio.microsoft.com/downloads) veya mevcut Visual Studio sürümünüzle yan yana yüklemek istediğiniz Ikincil sürümün [Visual Studio 2019 yayımları](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasından indirin.

1. Komut istemi 'ni yönetici modunda açın. Bunu yapmak için, Windows Başlat menüsünü açın, "cmd" yazın, komut Istemi arama sonuçlarına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. Komut isteminde dizinini, Visual Studio önyükleyici dosyanızın bulunduğu klasör olarak değiştirin.

1. Yükleme konumu için yeni bir klasör yolu belirterek ve .exe dosya adını yüklemekte olduğunuz Visual Studio sürümü için uygun önyükleyici adı ile değiştirerek aşağıdaki komutu çalıştırın. .exe dosya adı eşleşmelidir veya aşağıdaki dosyalardan birine benzer olmalıdır:

   * Visual Studio Enterprise için vs_enterprise.exe
   * Visual Studio Professional için vs_professional.exe
   * Visual Studio Community için vs_community.exe

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Yüklemeniz için gereken bileşenleri seçmek üzere Yükleyici iletişim kutularını izleyin. Daha fazla bilgi için bkz. [Visual Studio 'Yu yükler](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio 2022 önyükleyici dosyasını Visual Studio [İndirmeleri sayfasından](https://visualstudio.microsoft.com/downloads) veya mevcut Visual Studio sürümünüzle yan yana yüklemek istediğiniz Ikincil sürümün [Visual Studio 2022 yayımları](/visualstudio/releases/2022/history) sayfasından indirin.

1. Komut istemi 'ni yönetici modunda açın. Bunu yapmak için, Windows Başlat menüsünü açın, "cmd" yazın, komut Istemi arama sonuçlarına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. Komut isteminde dizinini, Visual Studio önyükleyici dosyanızın bulunduğu klasör olarak değiştirin.

1. Yükleme konumu için yeni bir klasör yolu belirterek ve .exe dosya adını yüklemekte olduğunuz Visual Studio sürümü için uygun önyükleyici adı ile değiştirerek aşağıdaki komutu çalıştırın. .exe dosya adı eşleşmelidir veya aşağıdaki dosyalardan birine benzer olmalıdır:

   * Visual Studio Enterprise için vs_enterprise.exe
   * Visual Studio Professional için vs_professional.exe
   * Visual Studio Community için vs_community.exe

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Yüklemeniz için gereken bileşenleri seçmek üzere Yükleyici iletişim kutularını izleyin. Daha fazla bilgi için bkz. [Visual Studio 'Yu yükler](install-visual-studio.md#step-4---choose-workloads).
   
::: moniker-end

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana Yüklemeler

Visual Basic, Visual C# ve Visual F# projeleri, projenin hangi .NET Framework sürümünü kullandığını belirtmek için **Proje tasarımcısında** **Target Framework** seçeneğini kullanır. Bir C++ projesi için. vcxproj dosyasını değiştirerek hedef çerçeveyi el ile değiştirebilirsiniz. Daha fazla bilgi için .NET Framework sayfasındaki [sürüm uyumluluğu](/dotnet/framework/migration-guide/version-compatibility) ' na bakın.

Bir proje oluşturduğunuzda, **Yeni proje** iletişim kutusundaki **.NET Framework** listesinde projenin hangi .NET Framework sürümünü hedeflediğini belirtebilirsiniz.

Dile özgü bilgiler için aşağıdaki tablodaki ilgili konuya bakın.

::: moniker range="vs-2017"

| Dil     | Konu                                                                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C#    | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true)                 |
| Visual F#    | [Visual Studio 'da Visual F# ile geliştirme](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true)                                               |
| C++          | [Nasıl yapılır: Hedef çerçeve ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/)                         |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [C/C++ yalıtılmış uygulamaları ve yan yana derlemeleri oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Dil     | Konu                                                                                                                           |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)         |
| Visual C#    | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)                         |
| Visual F#    | [Visual Studio 'da Visual F# ile geliştirme](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [Nasıl yapılır: Hedef çerçeve ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [C/C++ yalıtılmış uygulamaları ve yan yana derlemeleri oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

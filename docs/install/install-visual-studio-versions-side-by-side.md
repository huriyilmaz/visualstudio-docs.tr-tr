---
title: Visual Studio sürümlerini yan yana yükleme
description: Önceden yüklenmiş bir Visual Studio veya sonraki bir sürümü olan bir bilgisayara yükleme hakkında Visual Studio öğrenin.
ms.custom: SEO-VS-2020
ms.date: 03/29/2021
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.openlocfilehash: 01ba5330e94cc1d1c9f4056e2e23a254b83d3c33
ms.sourcegitcommit: 7a6358d7c7de0a7b9b9553801e72d91d972b0c94
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/08/2021
ms.locfileid: "129680102"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme

Önceki veya Visual Studio sürümünün yüklü olduğu bir bilgisayara yükleme Visual Studio yükleyebilirsiniz.

::: moniker range="vs-2017"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirebilirsiniz:

* Visual Studio 2015'te oluşturulmuş bir çözümü açmak için Visual Studio 2017 kullanıyorsanız, Visual Studio 2017'ye özgü hiçbir özellik uygulamadıysanız daha sonra önceki sürümde çözümü yeniden açıp değiştirebilirsiniz.

* Visual Studio 2015 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2017 kullanmayı denersanız, projelerinizi ve dosyalarınızı Visual Studio 2017 ile uyumlu olacak şekilde değiştirmeniz gerekir. Daha fazla bilgi için [Projelerde bağlantı noktası, geçiş ve yükseltme Visual Studio bakın.](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)

::: moniker-end

::: moniker range="vs-2019"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirebilirsiniz:

* Visual Studio 2017'de oluşturulmuş bir çözümü açmak için Visual Studio 2019 kullanıyorsanız, Visual Studio 2019'a özgü hiçbir özellik uygulamadıysanız çözümü daha sonra önceki sürümde yeniden açıp değiştirebilirsiniz.

* Visual Studio 2017 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2019 kullanmayı denersanız, projelerinizi ve dosyalarınızı Visual Studio 2019 ile uyumlu olacak şekilde değiştirmeniz gerekir. Daha fazla bilgi için [Projelerde bağlantı noktası, geçiş ve yükseltme Visual Studio bakın.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

::: moniker-end

::: moniker range=">=vs-2022"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirebilirsiniz:

* Visual Studio 2017 veya Visual Studio 2019'da oluşturulmuş bir çözümü açmak için Visual Studio 2022 kullanıyorsanız, Visual Studio 2022'ye özel hiçbir özellik uygulamadıysanız çözümü daha sonra önceki sürümde yeniden açıp değiştirebilirsiniz.

* Visual Studio 2019 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2022 kullanmayı denersanız, projelerinizi ve dosyalarınızı Visual Studio 2022 ile uyumlu olacak şekilde değiştirmeniz gerekir. Daha fazla bilgi için [Projelerde bağlantı noktası, geçiş ve yükseltme Visual Studio bakın.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

::: moniker-end

* Birden fazla sürümü yüklü bir bilgisayarda Visual Studio sürümünü kaldırırsanız, Visual Studio için dosya ilişkilendirmeleri tüm sürümler için kaldırılır.

* Visual Studio, tüm uzantılar uyumlu olduğundan uzantıları otomatik olarak yükseltmez. Uzantıları marketten veya yazılım Visual Studio [yeniden](https://marketplace.visualstudio.com/) yüklemeniz gerekir.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>Alt Visual Studio sürümlerini yan yana yükleme

Visual Studio'nin bir ikincil sürümünden bir sonraki sürüme yükseltirken, Visual Studio yükleyicisi varsayılan olarak geçerli yüklemenizi bu kanalda en son sürüme güncelleştirecek. Örneğin, 16.9.4'un yeni yayına hazır olduğunu varsayalım. Her iki sürüm de Visual Studio 2019 yayın kanalının bir parçası olduğu için yükleyici, geçerli 16.9.3 (veya daha düşük) yüklemenizi [16.9.4 ile değiştirmeyi dener.](/visualstudio/productinfo/release-rhythm) Güncelleştirme sırasında eski sürümün yeni sürümle değiştirilmesi, Visual Studio eski sürümlerinin makinenize yer bırakmaması için yardımcı olur. Ancak, bazı belirli durumlarda, uygulamanın farklı ikincil yayın sürümlerini Visual Studio yardımcı olabilir. Örneğin, aynı makinede hem 16.9.3 hem de 16.9.4 olması iyi olabilir.

::: moniker range="vs-2017"

1. Visual Studio 2017 sürüm 15.9 için en son önyükleyiciyi, mevcut Visual Studio sürümünüzle yan yana yüklemek istediğiniz sürümün önceki sürümleri sayfasından Visual Studio. [](https://visualstudio.microsoft.com/vs/older-downloads/)

1. Komut istemini yönetici modunda açın. Bunu yapmak için, Windows Başlat menüsü", "cmd" yazın, Komut İstemi arama sonuçlarına sağ tıklayın ve Yönetici olarak **çalıştır'ı seçin.** Komut isteminde dizini, önyükleyici dosyanızı Visual Studio klasör olarak değiştirebilirsiniz.

1. Aşağıdaki komutu çalıştırın ve yükleme konumu için yeni bir klasör yolu belirtin ve .exe dosya adını, yüklemekte olduğunuz dosyanın sürümü için uygun Visual Studio önyükleyici adıyla değiştirir. Dosya .exe adı aşağıdaki dosyalardan biri ile eşleşmeli veya benzerdir:

   * vs_enterprise.exe için Visual Studio Enterprise
   * vs_professional.exe için Visual Studio Professional

1. Yüklemeniz için gereken bileşenleri seçmek için yükleyici iletişim kutularını izleyin. Daha fazla bilgi için [bkz. Yükleme Visual Studio.](install-visual-studio.md#step-4---choose-workloads)

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 önyükleyici dosyasını [Visual Studio](https://visualstudio.microsoft.com/downloads) indirmeleri sayfasından veya mevcut Visual Studio sürümünüzle yan yana yüklemek istediğiniz ikincil sürümün Visual Studio [2019](/visualstudio/releases/2019/history#installing-an-earlier-release) Sürümler sayfasından indirin.

1. Komut istemini yönetici modunda açın. Bunu yapmak için, Windows Başlat menüsü", "cmd" yazın, Komut İstemi arama sonuçlarına sağ tıklayın ve Yönetici olarak **çalıştır'ı seçin.** Komut isteminde dizini, önyükleyici dosyanızı Visual Studio klasör olarak değiştirebilirsiniz.

1. Aşağıdaki komutu çalıştırın ve yükleme konumu için yeni bir klasör yolu belirtin ve .exe dosya adını, yüklemekte olduğunuz dosyanın sürümü için uygun Visual Studio önyükleyici adıyla değiştirir. Dosya .exe adı aşağıdaki dosyalardan biri ile eşleşmeli veya benzerdir:

   * vs_enterprise.exe için Visual Studio Enterprise
   * vs_professional.exe için Visual Studio Professional
   * vs_community.exe için Visual Studio Community

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Yüklemeniz için gereken bileşenleri seçmek için yükleyici iletişim kutularını izleyin. Daha fazla bilgi için [bkz. Yükleme Visual Studio.](install-visual-studio.md#step-4---choose-workloads)

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio indirmeleri sayfasından [Visual Studio](https://visualstudio.microsoft.com/downloads) 2022 önyükleyici dosyasını veya mevcut Visual Studio sürümünüzle yan yana yüklemek istediğiniz ikincil sürümün Visual Studio [2022](/visualstudio/releases/2022/release-notes-history) Sürümler sayfasından Visual Studio.

1. Komut istemini yönetici modunda açın. Bunu yapmak için, Windows Başlat menüsü", "cmd" yazın, Komut İstemi arama sonuçlarına sağ tıklayın ve Yönetici olarak **çalıştır'ı seçin.** Komut isteminde dizini, önyükleyici dosyanızı Visual Studio klasör olarak değiştirebilirsiniz.

1. Aşağıdaki komutu çalıştırın ve yükleme konumu için yeni bir klasör yolu belirtin ve .exe dosya adını, yüklemekte olduğunuz dosyanın sürümü için uygun Visual Studio önyükleyici adıyla değiştirir. Dosya .exe adı aşağıdaki dosyalardan biri ile eşleşmeli veya benzerdir:

   * vs_enterprise.exe için Visual Studio Enterprise
   * vs_professional.exe için Visual Studio Professional
   * vs_community.exe için Visual Studio Community

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Yüklemeniz için gereken bileşenleri seçmek için yükleyici iletişim kutularını izleyin. Daha fazla bilgi için [bkz. Yükleme Visual Studio.](install-visual-studio.md#step-4---choose-workloads)
   
::: moniker-end

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana yüklemeler

Visual Basic, Visual C# ve Visual F# **projeleri, Project Designer'daki** **Hedef** Çerçeve seçeneğini kullanarak projenin kullandığı .NET Framework sürümünü belirtir. Bir C++ projesi için .vcxproj dosyasını değiştirerek hedef çerçeveyi el ile değiştirebilirsiniz. Daha fazla bilgi için [bkz. Sürüm uyumluluğu .NET Framework.](/dotnet/framework/migration-guide/version-compatibility)

Bir proje ekleyebilirsiniz, Yeni .NET Framework iletişim kutusundaki .NET Framework hedeflerinin hangi  sürümünü **Project** belirtebilirsiniz.

Dile özgü bilgiler için aşağıdaki tabloda uygun konuya bakın.

::: moniker range="vs-2017"

| Dil     | Konu                                                                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C#    | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true)                 |
| Visual F#    | [Visual F#'de Visual Studio](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true)                                               |
| C++          | [Nasıl yapılır: Hedef çerçeve ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/)                         |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md?view=vs-2017&preserve-view=true)
* [Projeleri taşıma, geçirme ve Visual Studio yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true)
* [C/C++ yalıtılmış uygulamaları ve yan yana derlemeleri oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Dil     | Konu                                                                                                                           |
|--------------|---------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md)         |
| Visual C#    | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md)                         |
| Visual F#    | [Visual F#'de Visual Studio](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [Nasıl yapılır: Hedef çerçeve ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Projeleri taşıma, geçirme ve Visual Studio yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [C/C++ yalıtılmış uygulamaları ve yan yana derlemeleri oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

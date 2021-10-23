---
title: Visual Studio sürümlerini yan yana yükleme
description: daha önceki veya daha sonraki bir Visual Studio zaten yüklü bir bilgisayara Visual Studio yüklemeyi öğrenin.
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
ms.openlocfilehash: a4df127d6131f6121c68f9900f2af8a3f66da811
ms.sourcegitcommit: 0257750be796cc46e01cebd8976f637743d29417
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/23/2021
ms.locfileid: "130290648"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme

Visual Studio, daha önceki veya daha sonraki bir Visual Studio zaten yüklü bir bilgisayara yükleyebilirsiniz.

::: moniker range="vs-2017"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2015 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2017 ' ı kullanırsanız, daha sonra Visual Studio 2017 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra yeniden açabilir ve değiştirebilirsiniz.

* Visual Studio 2015 veya daha önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2017 ' ı kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2017 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. daha fazla bilgi için bkz. [bağlantı noktası, taşıma ve Visual Studio projeleri yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017&preserve-view=true) sayfası.

::: moniker-end

::: moniker range="vs-2019"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2017 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2019 ' ı kullanırsanız, daha sonra Visual Studio 2019 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra yeniden açabilir ve değiştirebilirsiniz.

* Visual Studio 2017 veya daha önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2019 ' ı kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2019 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. daha fazla bilgi için bkz. [bağlantı noktası, taşıma ve Visual Studio projeleri yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md) sayfası.

::: moniker-end

::: moniker range=">=vs-2022"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2017 veya Visual Studio 2019 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2022 ' ı kullanırsanız, daha sonra Visual Studio 2022 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra yeniden açabilir ve değiştirebilirsiniz.

* Visual Studio 2019 veya daha önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2022 ' ı kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2022 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. daha fazla bilgi için bkz. [bağlantı noktası, taşıma ve Visual Studio projeleri yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md) sayfası.

::: moniker-end

* birden fazla sürümü yüklü olan bir bilgisayarda Visual Studio sürümünü kaldırırsanız, Visual Studio için dosya ilişkilendirmeleri tüm sürümler için kaldırılır.

* tüm uzantılar uyumlu olmadığından Visual Studio uzantıları otomatik olarak yükseltmez. uzantıları [Visual Studio marketi](https://marketplace.visualstudio.com/) 'nden veya yazılım yayımcısından yeniden yüklemeniz gerekir.

## <a name="install-minor-visual-studio-versions-side-by-side"></a>ikincil Visual Studio sürümlerini yan yana yüklemeye

Visual Studio en düşük bir sürümüne yükseltirken, Visual Studio yükleyicisi varsayılan olarak geçerli yüklemenizi o kanaldaki en son sürüme güncelleştirir. Örneğin, 16.9.4 yeni bir yayın olduğunu varsayalım. her iki sürüm de [Visual Studio 2019 yayın kanalının](/visualstudio/productinfo/release-rhythm)bir parçası olduğundan, yükleyici geçerli 16.9.3 (veya daha düşük) yüklemenizi 16.9.4 ile değiştirmeye çalışır. güncelleştirme sırasında eski sürümü daha yeni sürümle değiştirmek, Visual Studio eski sürümlerinin makinenizde yer kaplamadığından emin olmanıza yardımcı olur. ancak bazı belirli durumlarda, Visual Studio yan yana farklı küçük yayın sürümlerini yüklemek yararlı olabilir. Örneğin, aynı makinede hem 16.9.3 hem de 16.9.4 olmak isteyebilirsiniz.

::: moniker range="vs-2017"

1. Visual Studio 2017 sürüm 15,9 için en son önyükleyici 'yi, mevcut Visual Studio sürümü ile yan yana yüklemek istediğiniz sürüm için [Visual Studio önceki sürümler](https://visualstudio.microsoft.com/vs/older-downloads/) sayfasından indirin.

1. Komut istemi 'ni yönetici modunda açın. bunu yapmak için Windows Başlat menüsü açın, "cmd" yazın, komut istemi arama sonuçlarına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. komut isteminde, dizin Visual Studio önyükleyici dosyanızın bulunduğu klasör olarak değiştirin.

1. yükleme konumu için yeni bir klasör yolu belirterek ve .exe dosya adını yüklemekte olduğunuz Visual Studio sürümüne uygun önyükleyici adı ile değiştirerek aşağıdaki komutu çalıştırın. .exe dosya adı eşleşmelidir veya aşağıdaki dosyalardan birine benzer olmalıdır:

   * Visual Studio Enterprise için vs_enterprise.exe
   * Visual Studio Professional için vs_professional.exe

1. Yüklemeniz için gereken bileşenleri seçmek üzere Yükleyici iletişim kutularını izleyin. Daha fazla bilgi için bkz. [ınstall Visual Studio](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range="vs-2019"

1. Visual Studio 2019 önyükleyici dosyasını [Visual Studio indirmeleri sayfasından](https://visualstudio.microsoft.com/downloads) veya mevcut Visual Studio sürümü ile yan yana yüklemek istediğiniz ikincil sürümün [Visual Studio 2019 yayınları](/visualstudio/releases/2019/history#installing-an-earlier-release) sayfasından indirin.

1. Komut istemi 'ni yönetici modunda açın. bunu yapmak için Windows Başlat menüsü açın, "cmd" yazın, komut istemi arama sonuçlarına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. komut isteminde, dizin Visual Studio önyükleyici dosyanızın bulunduğu klasör olarak değiştirin.

1. yükleme konumu için yeni bir klasör yolu belirterek ve .exe dosya adını yüklemekte olduğunuz Visual Studio sürümüne uygun önyükleyici adı ile değiştirerek aşağıdaki komutu çalıştırın. .exe dosya adı eşleşmelidir veya aşağıdaki dosyalardan birine benzer olmalıdır:

   * Visual Studio Enterprise için vs_enterprise.exe
   * Visual Studio Professional için vs_professional.exe
   * Visual Studio Community için vs_community.exe

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files (x86)\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Yüklemeniz için gereken bileşenleri seçmek üzere Yükleyici iletişim kutularını izleyin. Daha fazla bilgi için bkz. [ınstall Visual Studio](install-visual-studio.md#step-4---choose-workloads).

::: moniker-end

::: moniker range=">=vs-2022"

1. Visual Studio 2022 önyükleyici dosyasını [Visual Studio indirmeleri sayfasından](https://visualstudio.microsoft.com/downloads) veya mevcut Visual Studio sürümü ile yan yana yüklemek istediğiniz ikincil sürümün [Visual Studio 2022 yayınları](/visualstudio/releases/2022/release-notes) sayfasından indirin.

1. Komut istemi 'ni yönetici modunda açın. bunu yapmak için Windows Başlat menüsü açın, "cmd" yazın, komut istemi arama sonuçlarına sağ tıklayın ve **yönetici olarak çalıştır**' ı seçin. komut isteminde, dizin Visual Studio önyükleyici dosyanızın bulunduğu klasör olarak değiştirin.

1. yükleme konumu için yeni bir klasör yolu belirterek ve .exe dosya adını yüklemekte olduğunuz Visual Studio sürümüne uygun önyükleyici adı ile değiştirerek aşağıdaki komutu çalıştırın. .exe dosya adı eşleşmelidir veya aşağıdaki dosyalardan birine benzer olmalıdır:

   * Visual Studio Enterprise için vs_enterprise.exe
   * Visual Studio Professional için vs_professional.exe
   * Visual Studio Community için vs_community.exe

   ```shell
   vs_Enterprise.exe --installPath "C:\Program Files\Microsoft Visual Studio\<AddNewPath>"
   ```

1. Yüklemeniz için gereken bileşenleri seçmek üzere Yükleyici iletişim kutularını izleyin. Daha fazla bilgi için bkz. [ınstall Visual Studio](install-visual-studio.md#step-4---choose-workloads).
   
::: moniker-end

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana yüklemeler

Visual Basic, Visual C# ve Visual F# projeleri, bir projenin hangi .NET Framework sürümünü kullandığını belirtmek için **Project tasarımcısında** **Target Framework** seçeneğini kullanır. Bir C++ projesi için. vcxproj dosyasını değiştirerek hedef çerçeveyi el ile değiştirebilirsiniz. daha fazla bilgi için .NET Framework sayfasındaki [sürüm uyumluluğu](/dotnet/framework/migration-guide/version-compatibility) ' na bakın.

bir proje oluşturduğunuzda, **yeni Project** iletişim kutusundaki **.NET Framework** listesinde projenin hangi .NET Framework sürümünü hedeflediğini belirtebilirsiniz.

Dile özgü bilgiler için aşağıdaki tablodaki ilgili konuya bakın.

::: moniker range="vs-2017"

| Dil     | Konu                                                                                                                                                   |
|--------------|---------------------------------------------------------------------------------------------------------------------------------------------------------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017&preserve-view=true) |
| Visual C#    | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017&preserve-view=true)                 |
| Visual F#    | [Visual Studio Visual F# ile geliştirme](../ide/fsharp-visual-studio.md?view=vs-2017&preserve-view=true)                                               |
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
| Visual F#    | [Visual Studio Visual F# ile geliştirme](../ide/fsharp-visual-studio.md)                                                       |
| C++          | [Nasıl yapılır: Hedef çerçeve ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleme](install-visual-studio.md)
* [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [C/C++ yalıtılmış uygulamaları ve yan yana derlemeleri oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

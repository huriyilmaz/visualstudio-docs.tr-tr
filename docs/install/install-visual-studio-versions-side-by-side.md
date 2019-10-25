---
title: Visual Studio sürümlerini yan yana yükleme
ms.date: 03/05/2019
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.topic: conceptual
helpviewer_keywords:
- side-by-side installations [Visual Studio]
- Help [Visual Studio], installing
- install multiple versions of Visual Studio
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: b7fb1e057ffd9f3824fa1fe49e353fd54694da91
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888683"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme

Visual Studio 'Yu daha önceki veya sonraki bir Visual Studio sürümü yüklü olan bir bilgisayara yükleyebilirsiniz.

::: moniker range="vs-2017"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2015 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2017 kullanıyorsanız, Visual Studio 2017 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra eski sürümde açabilir ve değiştirebilirsiniz.

* Visual Studio 2015 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2017 ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2017 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017) sayfası.

::: moniker-end

::: moniker range=">= vs-2019"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2017 ' de oluşturulmuş bir çözümü açmak için Visual Studio 2019 kullanıyorsanız, Visual Studio 2019 'e özgü herhangi bir özelliği uygulamadığınız sürece çözümü daha sonra eski sürümde açabilir ve değiştirebilirsiniz.

* Visual Studio 2017 veya önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2019 ' i kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2019 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için bkz. [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md) sayfası.

::: moniker-end

* Birden fazla sürümünün yüklü olduğu bir bilgisayarda Visual Studio 'nun bir sürümünü kaldırırsanız, Visual Studio için dosya ilişkilendirmeleri tüm sürümler için kaldırılır.

* Tüm uzantılar uyumlu olmadığından, Visual Studio uzantıları otomatik olarak yükseltmez. Uzantıları [Visual Studio Market](https://marketplace.visualstudio.com/) veya yazılım yayımcısından yeniden yüklemeniz gerekir.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana Yüklemeler

Visual Basic, görsel C#ve görsel F# projeler, projenin hangi .NET Framework sürümünü kullandığını belirtmek Için **Proje tasarımcısında** **Target Framework** seçeneğini kullanır. Bir C++ proje için,. vcxproj dosyasını değiştirerek hedef çerçeveyi el ile değiştirebilirsiniz. Daha fazla bilgi için .NET Framework sayfasındaki [sürüm uyumluluğu](/dotnet/framework/migration-guide/version-compatibility) ' na bakın.

Bir proje oluşturduğunuzda, **Yeni proje** iletişim kutusundaki **.NET Framework** listesinde projenin hangi .NET Framework sürümünü hedeflediğini belirtebilirsiniz.

Dile özgü bilgiler için aşağıdaki tablodaki ilgili konuya bakın.

::: moniker range="vs-2017"

| Dil | Konu |
|--------------|-----------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Visual Studio 'da F# Visual ile geliştirme](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Nasıl yapılır: hedef Framework ve platform araç takımını değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md?view=vs-2017)
* [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [C/C++ yalıtılmış uygulamalar ve yan yana derlemeler oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Dil | Konu |
|--------------|-----------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Visual Studio 'da F# Visual ile geliştirme](../ide/fsharp-visual-studio.md) |
| C++ | [Nasıl yapılır: hedef Framework ve platform araç takımını değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio'yu yükleyin](install-visual-studio.md)
* [Visual Studio projelerini bağlantı noktası, geçirme ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [C/C++ yalıtılmış uygulamalar ve yan yana derlemeler oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end
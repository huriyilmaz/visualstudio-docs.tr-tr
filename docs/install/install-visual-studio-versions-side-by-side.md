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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 62acf1c5e8cab960d4b670f7a05481644e9ffc1e
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75594090"
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

* Tüm uzantıları uyumlu olmadığından visual Studio uzantıları otomatik olarak yükseltmez. Uzantılar'dan yeniden yüklemeniz gerekir [Visual Studio Market](https://marketplace.visualstudio.com/) veya yazılım yayımcısından.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana Yüklemeler

Visual Basic, görsel C#ve görsel F# projeler, projenin hangi .NET Framework sürümünü kullandığını belirtmek Için **Proje tasarımcısında** **Target Framework** seçeneğini kullanır. Bir C++ projesi için .vcxproj dosyasını değiştirerek hedef Framework'ü el ile değiştirebilirsiniz. Daha fazla bilgi için .NET Framework sayfasındaki [sürüm uyumluluğu](/dotnet/framework/migration-guide/version-compatibility) ' na bakın.

Bir proje oluşturduğunuzda, projenin hangi .NET Framework sürümünü hedefleyeceğini belirtebilirsiniz **.NET Framework** listesinde **yeni proje** iletişim kutusu.

Dile özgü bilgiler için aşağıdaki tabloda ilgili konuya bakın.

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

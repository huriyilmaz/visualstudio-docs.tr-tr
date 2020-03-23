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
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.openlocfilehash: 428c41a96de90494167d04ded8722d49c76afc71
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114652"
---
# <a name="install-visual-studio-versions-side-by-side"></a>Visual Studio sürümlerini yan yana yükleme

Visual Studio'nun daha önceki veya sonraki bir sürümü zaten yüklenmiş olan bir bilgisayara Visual Studio'u yükleyebilirsiniz.

::: moniker range="vs-2017"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2015'te oluşturulmuş bir çözümü açmak için Visual Studio 2017'yi kullanırsanız, Visual Studio 2017'ye özgü herhangi bir özelliği uygulamadığınız sürece çözümü önceki sürümde yeniden açabilir ve değiştirebilirsiniz.

* Visual Studio 2015'te veya daha önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2017'yi kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2017 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için [Port'a bakın, geçiş yap ve Visual Studio Projects sayfasını yükseltin.](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)

::: moniker-end

::: moniker range=">= vs-2019"

Sürümleri yan yana yüklemeden önce aşağıdaki koşulları gözden geçirin:

* Visual Studio 2017'de oluşturulmuş bir çözümü açmak için Visual Studio 2019'u kullanırsanız, Visual Studio 2019'a özgü herhangi bir özelliği uygulamadığınız sürece çözümü önceki sürümde yeniden açabilir ve değiştirebilirsiniz.

* Visual Studio 2017'de veya daha önceki bir sürümde oluşturulmuş bir çözümü açmak için Visual Studio 2019'u kullanmaya çalışırsanız, projelerinizi ve dosyalarınızı Visual Studio 2019 ile uyumlu olacak şekilde değiştirmeniz gerekebilir. Daha fazla bilgi için [Port'a bakın, geçiş yap ve Visual Studio Projects sayfasını yükseltin.](../porting/port-migrate-and-upgrade-visual-studio-projects.md)

::: moniker-end

* Birden fazla sürümü yüklü olan bir bilgisayarda Visual Studio'nun bir sürümünü yüklerseniz, Visual Studio için dosya ilişkilendirmeleri tüm sürümler için kaldırılır.

* Tüm uzantılar uyumlu olmadığından Visual Studio uzantıları otomatik olarak yükseltmez. [Visual Studio Marketplace](https://marketplace.visualstudio.com/) veya yazılım yayıncısı uzantılarıyeniden yüklemeniz gerekir.

## <a name="net-framework-versions-and-side-by-side-installations"></a>.NET Framework sürümleri ve yan yana kurulumlar

Visual Basic, Visual C#ve Visual F# projeleri, bir projenin hangi .NET Framework sürümünü kullandığını belirtmek için **Proje Tasarımcısı'ndaki** **Hedef Çerçeve** seçeneğini kullanır. Bir C++ projesi için .vcxproj dosyasını değiştirerek hedef çerçeveyi el ile değiştirebilirsiniz. Daha fazla bilgi için .NET Framework sayfasındaki [Sürüm uyumluluğuna](/dotnet/framework/migration-guide/version-compatibility) bakın.

Bir proje oluşturduğunuzda, **.NET** Framework'ün hangi sürümünü, proje hedeflerini yeni proje iletişim kutusunda **.NET Framework** listesinde belirtebilirsiniz.

Dile özgü bilgiler için aşağıdaki tabloda uygun konuya bakın.

::: moniker range="vs-2017"

| Dil | Konu başlığı |
|--------------|-----------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md?view=vs-2017) |
| Visual C# | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md?view=vs-2017) |
| Visual F# | [Visual Studio'da Visual F# ile geliştirin](../ide/fsharp-visual-studio.md?view=vs-2017) |
|C++ | [Nasıl yapilir: Hedef çerçeveyi ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md?view=vs-2017)
* [Visual Studio projelerini port, geçiş ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md?view=vs-2017)
* [C/C++ yalıtılmış uygulamalar ve yan yana derlemeler oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

::: moniker range=">= vs-2019"

| Dil | Konu başlığı |
|--------------|-----------|
| Visual Basic | [Uygulama Sayfası, Proje Tasarımcısı (Visual Basic)](../ide/reference/application-page-project-designer-visual-basic.md) |
| Visual C# | [Uygulama Sayfası, Proje Tasarımcısı (C#)](../ide/reference/application-page-project-designer-csharp.md) |
| Visual F# | [Visual Studio'da Visual F# ile geliştirin](../ide/fsharp-visual-studio.md) |
| C++ | [Nasıl yapilir: Hedef çerçeveyi ve platform araç kümesini değiştirme](/cpp/build/how-to-modify-the-target-framework-and-platform-toolset/) |

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Visual Studio yükleme](install-visual-studio.md)
* [Visual Studio projelerini port, geçiş ve yükseltme](../porting/port-migrate-and-upgrade-visual-studio-projects.md)
* [C/C++ yalıtılmış uygulamalar ve yan yana derlemeler oluşturma](/cpp/build/building-c-cpp-isolated-applications-and-side-by-side-assemblies/)

::: moniker-end

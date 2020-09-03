---
title: "Nasıl yapılır: Visual C++ projelerini Visual Studio 2015 'ye yükseltme | Microsoft Docs"
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- projects [C++], upgrading
ms.assetid: 9a283ebb-f6d8-49c0-a73e-323979ff56a2
caps.latest.revision: 26
author: corob-msft
ms.author: corob
manager: jillfra
ms.openlocfilehash: 23461fb1927cfcbf738d2dbcb82e3977b3be265a
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "77278735"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Nasıl Yapılır: Visual C++ Projelerini Visual Studio 2015'e Yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için son belgeleri için bkz. [Visual C++ taşıma ve Yükseltme Kılavuzu](/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Visual Studio 'nun önceki bir sürümünde oluşturulmuş bir Visual C++ projesini ilk kez açtığınızda projeyi güncelleştirmeniz istenebilir. İleti, Visual C++ derleyicisinin ve kitaplıklarının en son sürümüne yükseltmek isteyip istemediğinizi sorar. Yükseltme seçenekleri, [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] Projeyi oluşturmak için kullanılan sürümüne bağlıdır.

 ' [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] De oluşturulan projeleri açmak, düzenlemek ve oluşturmak için kullanabilirsiniz, [!INCLUDE[win8](../includes/win8-md.md)] [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] ancak yeni bir proje oluşturmak için [!INCLUDE[win8](../includes/win8-md.md)] kullanmanız gerekir [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] . (Bir proje oluşturmak için [!INCLUDE[win81](../includes/win81-md.md)] , kullanmanız gerekir [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] .)

 Bir Windows 10 projesi oluşturmak için, kullanmanız gerekir [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] .

 Projeyi güncelleştirmeniz istenmezse, projeyi yükseltmek için herhangi bir şey yapmanız gerekmez.

- Proje (. vcproj), daha eski bir sürümünde oluşturulduysa [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[vs2010](../includes/vs2010-md.md)] , projeyi güncelleştirmeniz gerekir.

- Proje (. vcxproj), ' de oluşturulduysa [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)]  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] veya [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] iki seçeneğiniz vardır:

  - Güncelleştirmeyi atlayabilirsiniz. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] , [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] SP1, veya ' deki Visual C++ araçlarına erişimi varsa, projeyi hiçbir değişiklik yapmadan yükler  [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)] [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] . Bu erişimi, projenin, sahip olduğu aynı makinede oluşturulduğu Visual Studio sürümünü yükleyerek sağlayabilirsiniz [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] . Daha fazla bilgi için bkz. [Visual Studio sürümlerini yan yana yükleme](../install/install-visual-studio-versions-side-by-side.md).

  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)]Bu konunun ilerleyen kısımlarında açıklanan değişiklikleri yapmasına izin vererek projeyi güncelleştirebilirsiniz. Çözümünüzde birden fazla Visual C++ projeniz varsa, bunların tümünü güncelleştirmeniz gerekir.

    > [!NOTE]
    > İlk sorulduğunda güncelleştirmeyi reddederseniz projeyi daha sonra **Proje** menüsünde **VC + + projesini güncelleştir** ' i seçerek güncelleştirebilirsiniz. Komut görünmezse, bir güncelleştirme gerekli değildir.

## <a name="upgrading-a-visual-c-project"></a>Visual C++ projesini yükseltme
 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]Projeyi otomatik olarak güncelleştirmesine izin verirseniz, bu değişiklikler yapılır:

- Projeyi [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] derleyicisini ve kitaplıkları kullanacak şekilde değiştirir (Platformaraç takımı = VisualStudio v140).

- [!INCLUDE[cppcli](../includes/cppcli-md.md)]Projeler için, TargetFrameworkVersion 'ı .NET Framework 4.5.2 olarak değiştirir.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Özel bir Platformaraç takımı ile çalışmaya devam etme
 İçinde özel bir Platformaraç takımı ile çalışmaya devam etmek istiyorsanız [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] , araç seti bir x86 makinesinde%ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ altında veya bir x64 makinede% ProgramFiles (x86)% \ MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ altında bulunmalıdır. Özel bir Platformaraç kümesi oluşturma hakkında daha fazla bilgi için, Visual C++ ekip blogu 'nda [C++ yerel çoklu sürüm hedeflemesi](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) konusuna bakın.

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio projelerini taşıma, geçirme ve yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) hakkında [kılavuz taşıma ve yükseltme Visual C++](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)

---
title: "Nasıl yapılır: Visual C++ projelerini Visual Studio 2015'e yükseltme | Microsoft Docs"
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
ms.sourcegitcommit: 68f893f6e472df46f323db34a13a7034dccad25a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/15/2020
ms.locfileid: "77278735"
---
# <a name="how-to-upgrade-visual-c-projects-to-visual-studio-2015"></a>Nasıl Yapılır: Visual C++ Projelerini Visual Studio 2015'e Yükseltme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Visual Studio 2017 için son belgeleri için bkz. [görsel C++ taşıma ve Yükseltme Kılavuzu](/cpp/porting/visual-cpp-porting-and-upgrading-guide).

Visual Studio'nun önceki bir sürümde oluşturulmuş bir Visual C++ projesini ilk kez açtığınızda, projeyi güncelleştirmeniz istenebilir. Visual C++ derleyicisi ve kitaplıkların en son sürümüne yükseltmek isteyip istemediğinizi soran ileti. Yükseltme seçenekleri, projeyi oluşturmak için kullanılan [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümüne bağlıdır.

 [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]' de oluşturulan [!INCLUDE[win8](../includes/win8-md.md)] projelerini açmak, düzenlemek ve derlemek için [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] kullanabilirsiniz, ancak yeni bir [!INCLUDE[win8](../includes/win8-md.md)] projesi oluşturmak için [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]kullanmanız gerekir. (Bir [!INCLUDE[win81](../includes/win81-md.md)] projesi oluşturmak için [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)]kullanmanız gerekir.)

 Bir Windows 10 projesi oluşturmak için [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]kullanmanız gerekir.

 Projeyi güncelleştirmeniz istenmezse, projeyi yükseltmek için herhangi bir şey yapmanız gerekmeyebilir.

- Proje (. vcproj) [!INCLUDE[vs2010](../includes/vs2010-md.md)]daha eski bir [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] sürümünde oluşturulduysa projeyi güncelleştirmeniz gerekir.

- Proje (. vcxproj) [!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)], [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]veya [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)] oluşturulduysa iki seçeneğiniz vardır:

  - Güncellemeyi atlayabilirsiniz. [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)], SP1, [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)]veya [!INCLUDE[vs_dev12](../includes/vs-dev12-md.md)][!INCLUDE[vs_dev10_long](../includes/vs-dev10-long-md.md)] içindeki görsel C++ araçlara erişimi olması halinde projeyi hiçbir değişiklik yapmadan yükler. Bu erişimi, projenin [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]olan aynı makinede oluşturulduğu Visual Studio sürümünü yükleyerek sağlayabilirsiniz. Daha fazla bilgi için bkz. [Visual Studio sürümlerini yan yana yükleme](../install/install-visual-studio-versions-side-by-side.md).

  - [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], bu konunun ilerleyen kısımlarında açıklanan değişiklikleri yapmasına izin vererek projeyi güncelleştirebilirsiniz. Çözümünüzde birden fazla Visual C++ projesi varsa tümünü güncelleştirmeniz gerekir.

    > [!NOTE]
    > İlk sorulduğunda güncelleştirmeyi reddederseniz projeyi daha sonra **Proje** menüsünde **VC + + projesini güncelleştir** ' i seçerek güncelleştirebilirsiniz. Komut görünmüyorsa, güncelleştirme gerekli değildir.

## <a name="upgrading-a-visual-c-project"></a>Bir Visual C++ projesini yükseltme
 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] projeyi otomatik olarak güncelleştirmesine izin verirseniz, bu değişiklikler yapılır:

- Projeyi [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)] derleyicisini ve kitaplıklarını kullanacak şekilde değiştirir (Platformaraç takımı = VisualStudio v140).

- [!INCLUDE[cppcli](../includes/cppcli-md.md)] projeler için TargetFrameworkVersion 'ı .NET Framework 4.5.2 olarak değiştirir.

## <a name="continuing-to-work-with-a-custom-platformtoolset"></a>Özel PlatformToolset ile çalışmaya devam etmesini
 [!INCLUDE[vs_dev14](../includes/vs-dev14-md.md)]bir özel Platformaraç takımı ile çalışmaya devam etmek istiyorsanız, araç takımının bir x86 makinesinde%ProgramFiles%\MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ altında veya bir x64 makinesinde% ProgramFiles (x86)% \ MSBuild\Microsoft.Cpp\v4.0\Platforms\Win32\PlatformToolsets\ altında bulunması gerekir. Özel bir platformaraç kümesi oluşturma hakkında daha fazla bilgi için C++ bkz [ C++ ](https://blogs.msdn.com/b/vcblog/archive/2009/12/08/c-native-multi-targeting.aspx) . görsel ekip bloguna yerel çoklu sürüm belirleme.

## <a name="see-also"></a>Ayrıca Bkz.
 Visual [Studio projelerini taşıma, geçirme ve yükseltme](../porting/porting-migrating-and-upgrading-visual-studio-projects.md) ile [görsel C++ taşıma ve Yükseltme Kılavuzu](https://msdn.microsoft.com/library/f5fbcc3d-aa72-41a6-ad9a-a706af2166fb)

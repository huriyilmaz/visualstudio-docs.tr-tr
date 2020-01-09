---
title: -UseEnv (devenv.exe)
ms.date: 01/10/2019
ms.topic: reference
f1_keywords:
- VC.Project.UseEnvVars.ExcludePath
- VC.Project.UseEnvVars.LibraryPath
- VC.Project.UseEnvVars.SourcePath
- VC.Project.UseEnvVars.Include
- VC.Project.UseEnvVars.Path
- VC.Project.UseEnvVars.ReferencePath
helpviewer_keywords:
- UseEnv switch
- /UseEnv Devenv switch
- Devenv, /UseEnv
ms.assetid: 2dd14603-a61b-42d2-ba31-427a0ee8a799
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 35808b27964b3ca8fa0488f1be2ce6dc5530b3dd
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75596402"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Visual Studio 'Yu başlatır ve derleme için belirli ortam değişkenlerini yükler.

> [!NOTE]
> Bu anahtar ile birlikte yüklenir **C++ ile masaüstü geliştirme** iş yükü.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments

- *SolutionName*

  Bir çözüm dosyasının tam yolu ve adı.

- *ProjectName*

  Bir proje dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, **VC + + dizinleri**için proje özellikleri Içindeki VISUAL Studio IDE 'yi etkiler. `/UseEnv` anahtarını belirtirseniz, **VC + + dizinleri** düğümü Path, ıNCLUDE, LıBPATH ve LIB ortam değişkenlerinin değerlerini gösterir. (Ayrıca, **kaynak dizinlerin** ve **Dışlanan dizinlerin**değerlerini gösterir.) Aksi halde düğüm, ortam değişkenlerini beş dizin değeriyle değiştirir: **yürütülebilir dizinler**, **dizinleri**, **başvuru dizinleri**, **kitaplık dizinleri**ve **kitaplık WinRT dizinleri**.

> [!TIP]
> Projeye sağ tıklayıp C++ **Özellikler**' i seçerek Proje özelliklerine erişirsiniz. **Özellik sayfaları** Iletişim kutusunda **yapılandırma özellikleri** ' ni ve ardından **VC + + dizinleri**' ni seçin.

Bu anahtarla bir proje adı belirtildiğinde araç, projenin üst çözümündeki tüm projeler için ortam değişkenlerini görüntüler.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio 'Yu başlatır ve `MySolution` çözümünün özellik sayfalarına ortam değişkenleri yükler.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VC + + dizinleri Özellik sayfası (Windows)](/cpp/build/reference/vcpp-directories-property-page)

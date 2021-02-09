---
title: -UseEnv (devenv.exe)
description: Visual Studio 'Yu başlatmak ve derleme için belirli ortam değişkenlerini yüklemek üzere UseEnv Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 88c37bbdf49fe1c73a3f087058256a2c58ae9602
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99889765"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Visual Studio 'Yu başlatır ve derleme için belirli ortam değişkenlerini yükler.

> [!NOTE]
> Bu anahtar, C++ iş yüküne **sahip masaüstü geliştirmeyle** birlikte yüklenir.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Bir çözüm dosyasının tam yolu ve adı.

- *ProjectName*

  Bir proje dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, **VC + + dizinleri** için proje özellikleri Içindeki VISUAL Studio IDE 'yi etkiler. `/UseEnv`Anahtarı belirtirseniz, **VC + + DIZINLERI** düğümü Path, INCLUDE, LıBPATH ve LIB ortam değişkenlerinin değerlerini gösterir. (Ayrıca, **kaynak dizinlerin** ve **Dışlanan dizinlerin** değerlerini gösterir.) Aksi halde düğüm, ortam değişkenlerini beş dizin değeriyle değiştirir: **yürütülebilir dizinler**, **dizinleri**, **başvuru dizinleri**, **kitaplık dizinleri** ve **kitaplık WinRT dizinleri**.

> [!TIP]
> C++ projesine sağ tıklayıp **Özellikler**' i seçerek Proje özelliklerine erişirsiniz. **Özellik sayfaları** Iletişim kutusunda **yapılandırma özellikleri** ' ni ve ardından **VC + + dizinleri**' ni seçin.

Bu anahtarla bir proje adı belirtildiğinde araç, projenin üst çözümündeki tüm projeler için ortam değişkenlerini görüntüler.

## <a name="example"></a>Örnek

Aşağıdaki örnek Visual Studio 'Yu başlatır ve ortam değişkenlerini çözümün özellik sayfalarına yükler `MySolution` .

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VC + + dizinleri Özellik sayfası (Windows)](/cpp/build/reference/vcpp-directories-property-page)

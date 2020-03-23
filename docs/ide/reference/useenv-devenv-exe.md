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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75596402"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Visual Studio'u başlatır ve derleme için belirli ortam değişkenlerini yükler.

> [!NOTE]
> Bu anahtar, **C++** iş yüküne sahip Masaüstü geliştirme ile yüklenir.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionName*

  Çözüm dosyasının tam yolu ve adı.

- *Projeadı*

  Proje dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu **anahtar, VC++ Dizinleri**için proje özelliklerinde Visual Studio IDE'yi etkiler. `/UseEnv` Anahtarı belirtirseniz, **VC++ Dizindüğümü** PATH, INCLUDE, LIBPATH ve LIB ortam değişkenleri değerlerini gösterir. (Ayrıca **Kaynak Dizinleri** ve **Dışlama Dizinleri**için değerleri gösterir.) Aksi takdirde, düğüm beş dizin değerleri ile ortam değişkenleri değiştirir: **Çalıştırılabilir Dizinler**, **Dahil Dizinler**, **Başvuru Dizinleri**, **Kütüphane Dizinleri**ve **Kitaplık WinRT Dizinleri**.

> [!TIP]
> Bir C++ projesine sağ tıklayarak ve **Özellikler'i**seçerek proje özelliklerine erişebilirsiniz. Özellik **Sayfaları** iletişim kutusunda **Yapılandırma Özellikleri'ni** ve ardından **VC++ Dizinlerini**seçin.

Bu anahtarla bir proje adı belirtildiğinde, araç projenin ana çözümündeki tüm projeler için ortam değişkenlerini görüntüler.

## <a name="example"></a>Örnek

Aşağıdaki örnek Visual Studio'yu başlatır ve ortam `MySolution` değişkenlerini çözümün özellik sayfalarına yükler.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VC++ Dizinler Özellik Sayfası (Windows)](/cpp/build/reference/vcpp-directories-property-page)

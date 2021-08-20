---
title: -UseEnv (devenv.exe)
description: Derleme için belirli ortam değişkenlerini başlatmak ve yüklemek üzere UseEnv devenv komut Visual Studio anahtarını kullanmayı öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: a8a2b8e0ed2c02a4d912eacd93c82236332e72c9
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122123755"
---
# <a name="useenv-devenvexe"></a>/UseEnv (devenv.exe)

Derleme Visual Studio ve belirli ortam değişkenlerini yükler.

> [!NOTE]
> Bu anahtar C++ ile **Masaüstü geliştirme iş yüküyle** birlikte yüklenir.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /UseEnv {SolutionName|ProjectName}
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Çözüm dosyasının tam yolu ve adı.

- *Projeadı*

  Proje dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar

Bu anahtar, VC++ Visual Studio proje özelliklerinde IDE'nin **performansını etkiler.** Anahtarı `/UseEnv` belirtirsiniz, **VC++ Dizinleri** düğümü PATH, INCLUDE, LIBPATH ve LIB ortam değişkenleri için değerleri gösterir. (Ayrıca Kaynak Dizinler ve **Dışlama Dizinleri** **değerlerini de gösterir.)** Aksi takdirde düğüm, ortam değişkenlerini beş dizin değeriyle değiştirir: **Yürütülebilir** Dizinler, Dizinleri Dahil Edin, **Başvuru** Dizinleri, Kitaplık Dizinleri ve Kitaplık **WinRT Dizinleri.**

> [!TIP]
> Bir C++ projesine sağ tıklar ve Özellikler'i seçerek proje özelliklerine **erişebilirsiniz.** Özellik Sayfaları **iletişim kutusunda** Yapılandırma Özellikleri'ne **ve ardından** **VC++ Dizinleri'ne tıklayın.**

Bu anahtarla bir proje adı belirtilirse, araç projenin üst çözümü içindeki tüm projeler için ortam değişkenlerini görüntüler.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio ve ortam değişkenlerini çözümün özellik sayfalarına `MySolution` yükler.

```shell
devenv.exe /useenv "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [VC++ Dizinleri Özellik Sayfası (Windows)](/cpp/build/reference/vcpp-directories-property-page)

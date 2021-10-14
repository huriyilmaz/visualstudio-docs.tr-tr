---
title: Kapsayıcılar için bilinen sorunlar
description: Bir kapsayıcıya yükleme sırasında ortaya çıkabilir bilinen sorunlar hakkında Visual Studio Derleme Araçları bilgi Windows edin.
ms.date: 02/18/2020
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: anandmeg
ms.author: meghaanand
manager: jmartens
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: c73bb14065a28e0bdfd15c80d25562b6d884e63c
ms.sourcegitcommit: 8fae163333e22a673fd119e1d2da8a1ebfe0e51a
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/13/2021
ms.locfileid: "129969482"
---
# <a name="known-issues-for-containers"></a>Kapsayıcılar için bilinen sorunlar

Bir Docker kapsayıcısı içine Visual Studio birkaç sorun vardır.

## <a name="windows-container"></a>Windows kapsayıcısı

Aşağıdaki bilinen sorunlar, bir kapsayıcıya Visual Studio Derleme Araçları yükleme Windows oluşur.

::: moniker range="vs-2017"

* görüntü tabanlı Visual Studio kapsayıcıya yükleme mcr.microsoft.com/windows/servercore:10.0.14393.1593. 10.0.14393 öncesi veya sonrasındaki Windows ile etiketlenmiş görüntülerin çalışması gerekir.

* Sdk 10.0.14393 veya önceki bir sürümü Windows yük olamaz. Bazı paketler yük devretmez ve bu paketlere bağımlı olan iş yükleri çalışmaz.

::: moniker-end

* Görüntüyü `-m 2GB` sağlarken geçiş (veya daha fazlası). Bazı iş yükleri yüklenirken varsayılan 1 GB'den daha fazla bellek gerektirir.
* Docker'ı varsayılan 20 GB'den büyük diskleri kullanmak üzere yapılandırma.
* Komut `--norestart` satırına geçiş. Bu yazma işlemiyle birlikte, kapsayıcının içindeki bir Windows yeniden başlatma girişiminde bulunan konak `ERROR_TOO_MANY_OPEN_FILES` geri döner.
* Görüntünizi doğrudan bir mcr.microsoft.com/windows/servercore temel alırsanız, .NET Framework düzgün yüklenmeyebilir ve yükleme hatası belirtemeyebilir. Yükleme tamamlandıktan sonra yönetilen kod çalıştırılamayabilirsiniz. Bunun yerine görüntülerinizi [microsoft/dotnet-framework:4.7.1 veya sonraki bir sürümüne](https://hub.docker.com/r/microsoft/dotnet-framework) temel edin. Örneğin, aşağıdakine benzer bir MSBuild ile birlikte bir hatayla karşı karşıdan alabilirsiniz:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): hata MSB6003: Belirtilen görev yürütülebilir dosyası "csc.exe" çalıştırılemedi. 'System.IO.FileSystem, Version=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' dosyası veya derlemesi ya da bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.

::: moniker range="vs-2017"

* 2017 Visual Studio 15.8 veya önceki bir sürümü (herhangi bir ürün) mcr.microsoft.com/windows/servercore:1809 yükleyebilirsiniz. Daha fazla bilgi edinmek için bkz. https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Derleme Araçları kapsayıcısı

Derleme Araçları kapsayıcısı kullanılırken aşağıdaki bilinen sorunlar oluşabilir. Sorunların düzelt olup olmadığını veya bilinen başka sorunlar olup olmadığını görmek için Geliştirici [hesabı'Community.](https://aka.ms/feedback/suggest?space=8)

* IntelliTrace, kapsayıcı [içindeki bazı senaryolarda](https://github.com/Microsoft/vstest/issues/940) çalışmayabilirsiniz.
* Windows için Docker'ın eski sürümlerinde, varsayılan kapsayıcı görüntüsü boyutu yalnızca 20 GB'tır ve Derleme Araçları'ya uymaz. Görüntü [boyutunu](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) 127 GB veya daha fazla olarak değiştirmek için yönergeleri izleyin.
Bir disk alanı sorunu onaylamak için günlük dosyalarını kontrol edin ve daha fazla bilgi edinin. Disk `vslogs\dd_setup_<timestamp>_errors.log` alanınız yeterli olursa dosyanız aşağıdakileri içerir: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)

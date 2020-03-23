---
title: Kapsayıcılar için bilinen sorunlar
description: Visual Studio Build Tools'u bir Windows kapsayıcısına yüklediğinizde oluşabilecek bilinen sorunlar hakkında daha fazla bilgi edinin.
ms.date: 02/18/2020
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: ornellaalt
ms.author: ornella
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: a864f1ef623197a44c7d816b051efd0106e86ece
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "77611133"
---
# <a name="known-issues-for-containers"></a>Kapsayıcılar için bilinen sorunlar

Visual Studio'u Docker konteynerine yüklerken birkaç sorun vardır.

## <a name="windows-container"></a>Windows kapsayıcısı

Visual Studio Build Tools'u bir Windows kapsayıcısına yüklediğinizde aşağıdaki bilinen sorunlar oluşur.

::: moniker range="vs-2017"

* Visual Studio'u görüntü microsoft/windowsservercore:10.0.14393.1593 tabanlı bir kapsayıcıya yükleyemezsiniz. 10.0.14393'ten önce veya sonra Windows sürümleriyle etiketlenmiş resimler çalışmalıdır.

* Windows SDK sürümünü 10.0.14393 veya daha önce yükleyemezsiniz. Bazı paketler yüklenmez ve bu paketlere bağlı iş yükleri çalışmaz.

::: moniker-end

* Görüntüyü `-m 2GB` oluştururken (veya daha fazla) geçirin. Bazı iş yükleri yüklendiğinde varsayılan 1 GB'tan daha fazla bellek gerektirir.
* Docker'ı varsayılan 20 GB'tan daha büyük diskler kullanacak şekilde yapılandırın.
* Komut `--norestart` satırını iletin. Bu yazı dan itibaren, kapsayıcı içinden bir Windows `ERROR_TOO_MANY_OPEN_FILES` kapsayıcıyeniden başlatmaya çalışırken ana bilgisayara döner.
* Resminizi doğrudan microsoft/windowsservercore'a temel alarsanız, .NET Framework düzgün yüklenmeyebilir ve yükleme hatası belirtilmeyebilir. Yönetilen kod yükleme tamamlandıktan sonra çalışmayabilir. Bunun yerine, resminizi [microsoft/dotnet-framework:4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) veya sonraki temeller. Örnek olarak, MSBuild ile oluştururken aşağıdakilere benzer bir hata görebilirsiniz:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets(84,5): hata MSB6003: Belirtilen görev yürütülebilir "csc.exe" çalıştırılamamadı. Dosya veya montaj 'System.IO.FileSystem, Sürüm=4.0.1.0, Culture=neutral, PublicKeyToken=b03f5f7f11d50a3a' veya bağımlılıklarından birini yükleyemedi. Sistem belirtilen dosyayı bulamıyor.

::: moniker range="vs-2017"

* Visual Studio 2017 sürümünü 15.8 veya daha önce (herhangi bir ürün) mcr.microsoft.com/windows/servercore:1809 veya daha sonra yükleyemezsiniz. Daha fazla bilgi edinmek için bkz. https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Yapı Araçları konteyneri

Yapı Araçları kapsayıcısı kullandığınızda aşağıdaki bilinen sorunlar oluşabilir. Sorunların giderilip düzeltilmedigini veya bilinen diğer https://developercommunity.visualstudio.comsorunlar olup olmadığını görmek için ziyaret edin.

* IntelliTrace, kapsayıcı içindeki [bazı senaryolarda](https://github.com/Microsoft/vstest/issues/940) çalışmayabilir.
* Windows için Docker'ın eski sürümlerinde varsayılan kapsayıcı görüntü boyutu yalnızca 20 GB'dır ve Yapı Araçları'na uymaz. Görüntü boyutunu 127 GB veya daha [fazlasına değiştirmek için yönergeleri](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) izleyin.
Bir disk alanı sorununu onaylamak için, daha fazla bilgi için günlük dosyalarını denetleyin. Disk `vslogs\dd_setup_<timestamp>_errors.log` alanınız biterse dosyanız aşağıdakileri içerir: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Visual Studio Build Tools iş yükü ve bileşen ilikleri](workload-component-id-vs-build-tools.md)

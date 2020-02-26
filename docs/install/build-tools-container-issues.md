---
title: Kapsayıcılar için bilinen sorunlar
description: Windows kapsayıcısına Visual Studio Derleme Araçları yüklediğinizde oluşabilecek bilinen sorunlar hakkında daha fazla bilgi edinin.
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
ms.sourcegitcommit: b873fce7ba40d825fcb59555360c002bbfcecd9e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/26/2020
ms.locfileid: "77611133"
---
# <a name="known-issues-for-containers"></a>Kapsayıcılar için bilinen sorunlar

Visual Studio 'Yu bir Docker kapsayıcısına yüklerken bazı sorunlar vardır.

## <a name="windows-container"></a>Windows kapsayıcısı

Windows kapsayıcısına Visual Studio Derleme Araçları yüklediğinizde aşağıdaki bilinen sorunlar oluşur.

::: moniker range="vs-2017"

* Visual Studio 'Yu Microsoft/windowsservercore: 10.0.14393.1593 görüntüsüne göre bir kapsayıcıya yükleyemezsiniz. 10.0.14393 önce veya sonrasında Windows sürümleriyle etiketlenen görüntülerin çalışması gerekir.

* Windows SDK sürüm 10.0.14393 veya önceki bir sürümü yükleyemezsiniz. Bazı paketler yüklenemez ve bu paketlere bağlı olan iş yükleri çalışmayacak.

::: moniker-end

* Görüntüyü oluştururken `-m 2GB` (veya daha fazla) geçirin. Bazı iş yükleri, yüklendiğinde varsayılan 1 GB 'den daha fazla bellek gerektirir.
* Docker 'ı varsayılan 20 GB 'tan daha büyük diskleri kullanacak şekilde yapılandırın.
* Komut satırında `--norestart` geçirin. Bu yazma itibariyle, kapsayıcı içinden bir Windows kapsayıcısını yeniden başlatmaya çalışmak konağa `ERROR_TOO_MANY_OPEN_FILES` döndürür.
* Görüntünüzü doğrudan Microsoft/windowsservercore 'a dayandırırsanız .NET Framework düzgün şekilde yüklenemeyebilir ve hiçbir yüklemesi hatası belirtilmez. Yönetilen kod, yüklemesi tamamlandıktan sonra çalışmayabilir. Bunun yerine, görüntünüzü [Microsoft/DotNet-Framework: 4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri bir sürüme dayandırın. Örnek olarak, aşağıdaki gibi MSBuild ile derlerken bir hata görebilirsiniz:

  > C:\BuildTools\MSBuild\15.0\bin\Roslyn\Microsoft.CSharp.Core.targets (84, 5): hata MSB6003: belirtilen "csc. exe" görev çalıştırılabilir dosyası çalıştırılamadı. Dosya veya derleme ' System. ıO. FileSystem, Version = 4.0.1.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' veya onun bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.

::: moniker range="vs-2017"

* Visual Studio 2017 sürüm 15,8 veya önceki bir sürümü (herhangi bir ürün) mcr.microsoft.com/windows/servercore:1809 veya üzeri bir sürüme yükleyemezsiniz. Daha fazla bilgi edinmek için bkz. https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Derleme araçları kapsayıcısı

Yapı araçları kapsayıcısını kullandığınızda aşağıdaki bilinen sorunlar ortaya çıkabilir. Sorunların giderilmiş olup olmadığını veya bilinen diğer sorunlar olup olmadığını görmek için https://developercommunity.visualstudio.comziyaret edin.

* IntelliTrace bir kapsayıcı içindeki [bazı senaryolarda](https://github.com/Microsoft/vstest/issues/940) çalışmayabilir.
* Docker for Windows eski sürümlerinde, varsayılan kapsayıcı görüntü boyutu yalnızca 20 GB olur ve derleme araçlarına sığmıyor. Görüntü boyutunu 127 GB veya daha fazla olacak şekilde [değiştirmek için yönergeleri](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) izleyin.
Bir disk alanı sorununu doğrulamak için daha fazla bilgi için günlük dosyalarına bakın. Disk alanı tükeniyor olmanız durumunda `vslogs\dd_setup_<timestamp>_errors.log` dosyanız şunları içerir: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)

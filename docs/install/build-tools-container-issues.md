---
title: Kapsayıcılar için bilinen sorunlar
description: Windows kapsayıcısına Visual Studio Derleme Araçları yüklediğinizde oluşabilecek bilinen sorunlar hakkında daha fazla bilgi edinin.
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
ms.openlocfilehash: f275ede57614f369628c3f9e3ae733569ad1b4d5
ms.sourcegitcommit: 215680b355cf613bfa125cf6b864c8bb5f2c71a5
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/15/2021
ms.locfileid: "132453834"
---
# <a name="known-issues-for-containers"></a>Kapsayıcılar için bilinen sorunlar

docker kapsayıcısına Visual Studio yüklerken bazı sorunlar vardır.

## <a name="windows-container"></a>Windows kapsayıcısı

bir Windows kapsayıcısına Visual Studio Derleme Araçları yüklediğinizde aşağıdaki bilinen sorunlar oluşur.

::: moniker range="vs-2017"

* ımage mcr.microsoft.com/windows/servercore:10.0.14393.1593 tabanlı bir kapsayıcıya Visual Studio yükleyemezsiniz. 10.0.14393 önce veya sonra Windows sürümleriyle etiketlenmiş görüntüler çalışmalıdır.

* Windows SDK sürüm 10.0.14393 veya önceki bir sürümü yükleyemezsiniz. Bazı paketler yüklenemez ve bu paketlere bağlı olan iş yükleri çalışmayacak.

::: moniker-end

* `-m 2GB`Görüntü oluştururken pass (veya daha fazla). Bazı iş yükleri, yüklendiğinde varsayılan 1 GB 'den daha fazla bellek gerektirir.
* Docker 'ı varsayılan 20 GB 'tan daha büyük diskleri kullanacak şekilde yapılandırın.
* `--norestart`Komut satırını geçirin. bu yazma itibariyle, kapsayıcının içinden bir Windows kapsayıcısını yeniden başlatmaya çalışmak konağa geri dönmeye çalışılıyor `ERROR_TOO_MANY_OPEN_FILES` .
* görüntünüzü doğrudan mcr.microsoft.com/windows/servercore üzerinde temel alırsanız .NET Framework düzgün şekilde yüklenemeyebilir ve hiçbir yüklemesi hatası belirtilmez. Yönetilen kod, yüklemesi tamamlandıktan sonra çalışmayabilir. Bunun yerine, görüntünüzü [Microsoft/DotNet-Framework: 4.7.1](https://hub.docker.com/r/microsoft/dotnet-framework) veya üzeri bir sürüme dayandırın. örnek olarak, aşağıdakine benzer MSBuild ile derlerken bir hata görebilirsiniz:

  > c:\buildaraçları \ MSBuild \15.0\bin\Roslyn\Microsoft.CSharp.Core.targets (84, 5): error MSB6003: belirtilen "csc.exe" görev çalıştırılabilir dosyası çalıştırılamadı. Dosya veya derleme ' System. ıO. FileSystem, Version = 4.0.1.0, Culture = neutral, PublicKeyToken = b03f5f7f11d50a3a ' veya onun bağımlılıklarından biri yüklenemedi. Sistem belirtilen dosyayı bulamıyor.

::: moniker range="vs-2017"

* mcr.microsoft.com/windows/servercore:1809 veya sonraki sürümlere Visual Studio 2017 sürüm 15,8 veya önceki bir sürümü (herhangi bir ürün) yükleyemezsiniz. Daha fazla bilgi edinmek için bkz. https://aka.ms/setup/containers/servercore1809.

::: moniker-end

## <a name="build-tools-container"></a>Derleme araçları kapsayıcısı

Yapı araçları kapsayıcısını kullandığınızda aşağıdaki bilinen sorunlar ortaya çıkabilir. Sorunların giderilmiş olup olmadığını görmek için veya bilinen diğer sorunlar varsa, [geliştirici Community](https://aka.ms/feedback/suggest?space=8)ziyaret edin.

* IntelliTrace bir kapsayıcı içindeki [bazı senaryolarda](https://github.com/Microsoft/vstest/issues/940) çalışmayabilir.
* Docker for Windows eski sürümlerinde, varsayılan kapsayıcı görüntü boyutu yalnızca 20 GB olur ve derleme araçlarına sığmıyor. Görüntü boyutunu 127 GB veya daha fazla olacak şekilde [değiştirmek için yönergeleri](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) izleyin.
Bir disk alanı sorununu doğrulamak için daha fazla bilgi için günlük dosyalarına bakın. `vslogs\dd_setup_<timestamp>_errors.log`Disk alanı tükeniyor olmanız durumunda dosyanıza aşağıdakiler dahil edilir: 
```
Pre-check verification: Visual Studio needs at least 91.99 GB of disk space. Try to free up space on C:\ or change your target drive.
Pre-check verification failed with error(s) :  SizePreCheckEvaluator.
```
[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)

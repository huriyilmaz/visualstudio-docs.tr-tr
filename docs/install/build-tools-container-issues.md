---
title: Kapsayıcılar için bilinen sorunlar
description: Windows kapsayıcısına Visual Studio Derleme Araçları yüklediğinizde oluşabilecek bilinen sorunlar hakkında daha fazla bilgi edinin.
ms.date: 07/03/2019
ms.custom: seodec18
ms.topic: conceptual
ms.assetid: 140083f1-05bc-4014-949e-fb5802397c7a
author: heaths
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.prod: visual-studio-windows
ms.technology: vs-installation
ms.openlocfilehash: 2433f18f9980657ced5f5ddb274f5aa2a7671a60
ms.sourcegitcommit: 978df2feb5e64228d2e3dd430b299a5c234cda17
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72888605"
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

Yapı araçları kapsayıcısını kullandığınızda aşağıdaki bilinen sorunlar ortaya çıkabilir. Sorunların giderilmiş olup olmadığını veya bilinen diğer sorunlar olup olmadığını görmek için https://developercommunity.visualstudio.com ziyaret edin.

* IntelliTrace bir kapsayıcı içindeki [bazı senaryolarda](https://github.com/Microsoft/vstest/issues/940) çalışmayabilir.
* Docker for Windows eski sürümlerinde, varsayılan kapsayıcı görüntü boyutu yalnızca 20 GB olur ve derleme araçlarına sığmıyor. Görüntü boyutunu 127 GB veya daha fazla olacak şekilde [değiştirmek için yönergeleri](/virtualization/windowscontainers/manage-containers/container-storage#storage-limits) izleyin.

[!INCLUDE[install_get_support_md](includes/install_get_support_md.md)]

## <a name="see-also"></a>Ayrıca bkz.

* [Derleme Araçlarını Bir Kapsayıcıya Yükleme](build-tools-container.md)
* [Kapsayıcılar için İleri Düzey Örnek](advanced-build-tools-container.md)
* [Visual Studio Derleme Araçları iş yükü ve bileşen kimlikleri](workload-component-id-vs-build-tools.md)

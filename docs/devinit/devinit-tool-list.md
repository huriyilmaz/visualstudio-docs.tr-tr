---
title: Kullanılabilir araçlar
description: Geliştirme ortamını özelleştirmek için kullanılabilen tüm devinit araçlarının listesi.
ms.date: 02/08/2021
ms.topic: reference
author: andysterland
ms.author: andster
manager: jmartens
ms.workload:
- multiple
monikerRange: '>= vs-2019'
ms.prod: visual-studio-windows
ms.technology: devinit
ms.openlocfilehash: 482e838edf47d63235f60f013bd18eff586f83e8
ms.sourcegitcommit: 3fc099cdc484344c781f597581f299729c6bfb10
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/19/2021
ms.locfileid: "104672202"
---
# <a name="available-tools"></a>Kullanılabilir araçlar

> [!IMPORTANT]
> 12 Nisan 2021 itibariyle, Visual Studio 2019 ' den GitHub Codespaces 'a bağlanmak artık desteklenmeyecektir ve bu özel önizleme sona ermiştir. Bulut destekli bir iç döngü ve çok sayıda Visual Studio iş yükü için iyileştirilmiş VDı çözümleri için gelişen deneyimlere odaklanıyoruz. Bu `devinit` ve ilişkili araçların bir parçası olarak artık kullanılabilir olmayacaktır. Gelecekteki önizlemeler ve yol haritası bilgileri hakkında bilgi için, Visual Studio için geliştirici topluluğu forumumuza dahil etmeniz önerilir.

Aşağıdaki tabloda devınit için şu anda kullanılabilir olan araçların bir listesi bulunur.

| Araç                                                                                             | Açıklama                                                                                                 |
|--------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------|
| [**azurecli-login**](tool-azurecli-login.md)                                                     | Azure CLı komutunu yürütecek araç `az login --device-code` .                                             |
| [**choco-install**](tool-choco-install.md)                                                       | Chocolatey paketlerini yüklemek için araç.                                                                        |
| [**choco-upgrade**](tool-choco-upgrade.md)                                                       | Chocolatey paketlerini yükseltmek için araç.                                                                        |
| [**dotnet-restore**](tool-dotnet-restore.md)                                                     | Bir .NET projesinin bağımlılıklarını ve araçlarını geri yükleme aracı.                                               |
| [**dotnet-toolinstall**](tool-dotnet-toolinstall.md)                                             | .NET Core araçları 'nı yüklemeye yönelik araç (örneğin,. DotNet-EF)                                                |
| [**enable-iis**](tool-enable-iis.md)                                                             | IIS özelliklerini etkinleştirme ve en son ASP.NET barındırma paketini yüklemeye yönelik araç.                                  |
| [**msi-install**](tool-msi-install.md)                                                           | Bir yol veya URL 'ye verilen MSI dosyalarını yüklemeye yönelik araç.                                                              |
| [**npm-install**](tool-npm-install.md)                                                           | NPM paketlerini yüklemek için araç.                                                                               |
| [**nuget-restore**](tool-nuget-restore.md)                                                       | NuGet paketlerini geri yüklemeye yönelik araç.                                                                         |
| [**require-azureartifactscredentialprovider**](tool-require-azureartifactscredentialprovider.md) | Azure Artifacts kimlik bilgileri sağlayıcısını kurar.                                                           |
| [**require-azurecli**](tool-require-azurecli.md)                                                 | Azure CLı 'yı yüklemek için araç.                                                                              |
| [**require-dotnetcoresdk**](tool-require-dotnetcoresdk.md)                                       | .NET Core SDK ve paylaşılan çalışma zamanını yükleyen araç.                                                       |
| [**require-dotnetframeworksdk**](tool-require-dotnetframeworksdk.md)                             | .NET Framework SDK 'Yı yüklemek için araç.                                                                     |
| [**require-mssql**](tool-require-mssql.md)                                                       | MS SQL Server 2019 yüklemek için araç.                                                                         |
| [**require-nodejs**](tool-require-nodejs.md)                                                     | NodeJS ve NPM 'yi yüklemek için araç.                                                                             |
| [**require-nuget**](tool-require-nuget.md)                                                       | NuGet 'i yüklemeye yönelik araç.                                                                                      |
| [**require-npm**](tool-require-npm.md)                                                           | NPM 'yi yüklemek için araç.                                                                                        |
| [**require-psmodule**](tool-require-psmodule.md)                                                 | Galeriden PowerShell modülleri yüklemek için araç.                                                        |
| [**require-vcpkg**](tool-require-vcpkg.md)                                                       | Vcpkg 'yi yüklemek için araç.                                                                                      |
| [**require-vscomponent**](tool-require-vscomponent.md)                                           | Bir dosya temelinde VS yüklemelerini değiştirme aracı `.vsconfig` .                                                |
| [**gerektir-Winget**](tool-require-winget.md)                                                     | Winget 'i yüklemeye yönelik araç.                                                                                     |
| [**windowsfeature-enable**](tool-windowsfeature-enable.md)                                       | Araç kümesi Windows özelliklerini etkinleştir.                                                                           |
| [**windowsfeature-disable**](tool-windowsfeature-disable.md)                                     | Araç kümesi Windows özelliklerini devre dışı bırak.                                                                          |
| [**windowsfeature-list**](tool-windowsfeature-list.md)                                           | Tüm Windows özelliklerinin etkinleştir/devre dışı bırak durumunu listelemek için araç.                                              |
| [**set-env**](tool-set-env.md)                                                                   | Ortam değişkenlerini görüntüleme ve ayarlamaya yönelik araç.                                                                 |
| [**vcpkg-install**](tool-vcpkg-install.md)                                                       | Vcpkg aracılığıyla paket yüklemeye yönelik araç.                                                                         |
| [**Winget-Install**](tool-winget-install.md)                                                     | Winget aracılığıyla paket yüklemeye yönelik araç.                                                                        |
| [**wsl-install**](tool-wsl-install.md)                                                           | Linux için Windows alt sistemi için Linux Distro 'lara 'yi yüklemek ve yapılandırmak için araç.                             |

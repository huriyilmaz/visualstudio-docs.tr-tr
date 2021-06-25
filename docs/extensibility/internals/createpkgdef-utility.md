---
title: CreatePkgDef Yardımcı Programı | Microsoft Docs
description: Parametre olarak bir Visual Studio uzantısı için bir .dll dosyası alan ve .dll dosyasıyla eşlik edecek bir .pkgdef dosyası oluşturan CreatePkgDef yardımcı programı hakkında bilgi .dll öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: bfbd4b42d9ceddd40e08c28926a59aecba719fe9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898129"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef yardımcı programı
parametre olarak .dll uzantısı için bir Visual Studio dosyası alır ve dosyanın eşlik etmesi için *bir .pkgdef* *.dll* oluşturur. *.pkgdef* dosyası, uzantı yüklenirken aksi takdirde sistem kayıt defterine yazabilecek tüm bilgileri içerir.

> [!NOTE]
> Visual Studio SDK'sı içinde yer alan proje şablonlarının çoğu derleme işleminin bir parçası olarak otomatik olarak *.pkgdef* dosyaları oluşturur. Bu belge, el ile paket oluşturmak veya mevcut paketleri *.pkgdef*  dağıtımını kullanmak üzere dönüştürmek isteyen kullanıcılara yöneliktir.

## <a name="syntax"></a>Söz dizimi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Bağımsız değişkenler
**/out= &lt; DosyaAdı&gt;**\
Gereklidir. *.pkgdef çıkış dosyasının adını* &lt; FileName olarak &gt; ayarlar.

**/codebase**\
İsteğe bağlı. CodeBase yardımcı **programıyla kaydı** güçler.

**/assembly**\
Derleme yardımcı **programıyla kaydı** güçler.

**&lt;Assemblypath&gt;**\
*.pkgdef* *.dll* istediğiniz dosyanın yolu.

## <a name="remarks"></a>Açıklamalar
*.pkgdef dosyalarını kullanarak uzantı dağıtımı,* önceki sürümlerinin kayıt defteri gereksinimlerini Visual Studio.

::: moniker range=">=vs-2019"

*.pkgdef* dosyalarının aşağıdaki konumlardan biri içinde yüklü olması gerekir:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Yükleme klasörü *%localappdata%\Microsoft\Visual Studio\16.0\Extensions \\* ise, uzantı Visual Studio tarafından tanınır ancak varsayılan olarak devre dışıdır. Kullanıcı, Uzantıları Yönet'i kullanarak **uzantıyı etkinleştirerek.**

Yükleme klasörü *%vsinstalldir%\Common7\IDE\Extensions \\* ise uzantı varsayılan olarak etkindir.

> [!NOTE]
> Uzantıları **Yönet aracı,** vsIX paketinin bir parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

*.pkgdef* dosyalarının aşağıdaki konumlardan biri içinde yüklü olması gerekir:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%vsinstalldir%\Common7\IDE\Extensions\\*

Yükleme klasörü *%localappdata%\Microsoft\Visual Studio\15.0\Extensions \\* ise, uzantı Visual Studio tarafından tanınır ancak varsayılan olarak devre dışıdır. Kullanıcı Uzantılar ve Güncelleştirmeler'i **kullanarak uzantıyı etkinleştirerek.**

Yükleme klasörü *%vsinstalldir%\Common7\IDE\Extensions \\* ise uzantı varsayılan olarak etkindir.

> [!NOTE]
> Uzantılar **ve Güncelleştirmeler** aracı, vsIX paketinin bir parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [CreateExpInstance yardımcı programı](../../extensibility/internals/createexpinstance-utility.md)

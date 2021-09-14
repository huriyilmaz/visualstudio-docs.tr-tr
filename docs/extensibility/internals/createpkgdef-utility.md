---
title: CreatePkgDef yardımcı programı | Microsoft Docs
description: bir Visual Studio uzantısı için bir .dll dosyasını parametre olarak alan ve .dll dosyasına eşlik eden bir. pkgdef dosyası oluşturan CreatePkgDef yardımcı programı hakkında bilgi edinin.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 17e561a155e13b7857573894041e79e4d6ca90c1
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626162"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef yardımcı programı
bir Visual Studio uzantısı için bir .dll dosyasını parametre olarak alır ve *.dll* dosyasına eşlik eden bir *. pkgdef* dosyası oluşturur. *. Pkgdef* dosyası, uzantı yüklendiğinde sistem kayıt defterine yazılabilecek tüm bilgileri içerir.

> [!NOTE]
> Visual Studio SDK 'ya dahil edilen proje şablonlarının çoğu, yapı sürecinin bir parçası olarak *. pkgdef* dosyalarını otomatik olarak oluşturur. Bu belge, paketleri el ile oluşturmak isteyen veya var olan paketleri *. pkgdef*  dağıtımını kullanacak şekilde dönüştürecek şekilde hazırlanmıştır.

## <a name="syntax"></a>Söz dizimi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Bağımsız değişkenler
**/Out = &lt; filename&gt;**\
Gereklidir. *. Pkgdef* çıkış dosyasının adını filename olarak ayarlar &lt; &gt; .

**/CodeBase**\
İsteğe bağlı. **Kod temeli** yardımcı programıyla kayıt işlemini zorlar.

**/Assembly**\
**Derleme** yardımcı programıyla kayıt işlemini zorlar.

**&lt;AssemblyPath&gt;**\
*. Pkgdef* oluşturmak istediğiniz *.dll* dosyanın yolu.

## <a name="remarks"></a>Açıklamalar
*. Pkgdef* dosyaları kullanılarak Uzantı dağıtımı, Visual Studio önceki sürümlerinin kayıt defteri gereksinimlerinin yerini alır.

::: moniker range=">=vs-2019"

*. Pkgdef* dosyalarının aşağıdaki konumlardan birinde yüklü olması gerekir:

- *%localappdata%\microsoft\ Visual Studio \16.0\extensions\\*

- *%VSInstallDir%\common7\ide\extensions\\*

yükleme klasörü *%localappdata%\microsoft\ Visual Studio \16.0\extensions \\* ise, uzantı Visual Studio tarafından tanınır ancak varsayılan olarak devre dışıdır. Kullanıcı, **Uzantıları Yönet**' i kullanarak uzantıyı etkinleştirebilir.

Yükleme klasörü *%VSInstallDir%\common7\ide\extensions \\* ise, uzantı varsayılan olarak etkinleştirilir.

> [!NOTE]
> **Uzantıları Yönet** Aracı, bir VSIX paketinin parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

*. Pkgdef* dosyalarının aşağıdaki konumlardan birinde yüklü olması gerekir:

- *%localappdata%\microsoft\ Visual Studio \15.0\extensions\\*

- *%VSInstallDir%\common7\ide\extensions\\*

yükleme klasörü *%localappdata%\microsoft\ Visual Studio \15.0\extensions \\* ise, uzantı Visual Studio tarafından tanınır ancak varsayılan olarak devre dışıdır. Kullanıcı **uzantıları ve güncelleştirmeleri** kullanarak uzantıyı etkinleştirebilir.

Yükleme klasörü *%VSInstallDir%\common7\ide\extensions \\* ise, uzantı varsayılan olarak etkinleştirilir.

> [!NOTE]
> **Uzantılar ve güncelleştirmeler** Aracı, bir VSIX paketinin parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [CreateExpInstance yardımcı programı](../../extensibility/internals/createexpinstance-utility.md)

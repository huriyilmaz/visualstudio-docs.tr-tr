---
title: CreatePkgDef yardımcı programı | Microsoft Docs
description: Visual Studio uzantısı için bir. dll dosyasını parametre olarak alan ve. dll dosyasına eşlik etmek için bir. pkgdef dosyası oluşturan CreatePkgDef yardımcı programı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package definition
- create pkgdef
- pkgdef
- createpkgdef
ms.assetid: c745cb76-47a6-49ff-9eed-16af0f748e35
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: aa0b0e3e8ea59ce1d41f9d8a6c056239f2bc0e9a
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305551"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef yardımcı programı
Visual Studio uzantısı için bir. dll dosyasını parametre olarak alır ve. *DLL* dosyasına eşlik etmek için bir *. pkgdef* dosyası oluşturur. *. Pkgdef* dosyası, uzantı yüklendiğinde sistem kayıt defterine yazılabilecek tüm bilgileri içerir.

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
*. Pkgdef* oluşturmak istediğiniz *. dll* dosyasının yolu.

## <a name="remarks"></a>Açıklamalar
*. Pkgdef* dosyaları kullanılarak Uzantı dağıtımı, Visual Studio 'nun önceki sürümlerindeki kayıt defteri gereksinimlerinin yerini alır.

::: moniker range=">=vs-2019"

*. Pkgdef* dosyalarının aşağıdaki konumlardan birinde yüklü olması gerekir:

- *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*

- *%VSInstallDir%\common7\ide\extensions\\*

Yükleme klasörü *%localappdata%\Microsoft\Visual Studio\16.0\Extensions \\* Ise, uzantı Visual Studio tarafından tanınır ancak varsayılan olarak devre dışıdır. Kullanıcı, **Uzantıları Yönet**' i kullanarak uzantıyı etkinleştirebilir.

Yükleme klasörü *%VSInstallDir%\common7\ide\extensions \\* ise, uzantı varsayılan olarak etkinleştirilir.

> [!NOTE]
> **Uzantıları Yönet** Aracı, bir VSIX paketinin parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

*. Pkgdef* dosyalarının aşağıdaki konumlardan birinde yüklü olması gerekir:

- *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*

- *%VSInstallDir%\common7\ide\extensions\\*

Yükleme klasörü *%localappdata%\Microsoft\Visual Studio\15.0\Extensions \\* Ise, uzantı Visual Studio tarafından tanınır ancak varsayılan olarak devre dışıdır. Kullanıcı **uzantıları ve güncelleştirmeleri** kullanarak uzantıyı etkinleştirebilir.

Yükleme klasörü *%VSInstallDir%\common7\ide\extensions \\* ise, uzantı varsayılan olarak etkinleştirilir.

> [!NOTE]
> **Uzantılar ve güncelleştirmeler** Aracı, bir VSIX paketinin parçası olarak yüklenmediği sürece bir uzantıya erişmek için kullanılamaz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [CreateExpInstance yardımcı programı](../../extensibility/internals/createexpinstance-utility.md)

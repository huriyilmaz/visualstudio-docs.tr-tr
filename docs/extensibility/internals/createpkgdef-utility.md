---
title: CreatePkgDef Yardımcı Programı | Microsoft Dokümanlar
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
ms.openlocfilehash: 9f437eb3586dc16bb0b4b9eb60cd303eb90db6c3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709163"
---
# <a name="createpkgdef-utility"></a>CreatePkgDef yardımcı programı
Bir .dll dosyasını parametre olarak Visual Studio uzantısı için alır ve *.dll* dosyasına eşlik edecek bir *.pkgdef* dosyası oluşturur. *.pkgdef* dosyası, uzantı yüklendiğinde sistem kayıt defterine yazılması gereken tüm bilgileri içerir.

> [!NOTE]
> Visual Studio SDK'da yer alan proje şablonlarının çoğu, yapı işleminin bir parçası olarak otomatik olarak *.pkgdef* dosyaları oluşturur. Bu belge, paketleri el ile oluşturmak veya varolan paketleri *.pkgdef* dağıtımını kullanmak üzere dönüştürmek isteyenler için tasarlanmıştır.

## <a name="syntax"></a>Sözdizimi

```
CreatePkgDef /out=<FileName> [/codebase] [/assembly] <AssemblyPath>
```

## <a name="arguments"></a>Bağımsız Değişkenler
**/out=&lt;FileName&gt;**\
Gereklidir. *.pkgdef* çıktı dosyasının adını &lt;FileName&gt;olarak ayarlar.

**/codebase**\
İsteğe bağlı. **CodeBase** yardımcı programı ile kayıt kuvvetleri.

**/montaj**\
**Meclis** programı ile kayıt zorlar.

**&lt;Assemblypath&gt;**\
*.pkgdef'i*oluşturmak istediğiniz *.dll* dosyasının yolu.

## <a name="remarks"></a>Açıklamalar
*.pkgdef* dosyalarını kullanarak genişletme dağıtımı Visual Studio'nun önceki sürümlerinin kayıt defteri gereksinimlerinin yerini alır.

::: moniker range=">=vs-2019"

*.pkgdef* dosyaları aşağıdaki konumlardan birine yüklenmelidir:

- *%localappdata%\Microsoft\Visual Studio\16.0\Uzantılar\\*

- *%vsinstalldir%\Common7\IDE\Uzantılar\\*

Yükleme klasörü *%localappdata%\Microsoft\Visual Studio\16.0\Extensions\\*ise, uzantı Visual Studio tarafından tanınır, ancak varsayılan olarak devre dışı bırakılır. Kullanıcı **Uzantıları Yönet'i**kullanarak uzantıyı etkinleştirebilir.

Yükleme klasörü *%vsinstalldir%\Common7\IDE\Extensions\\*ise, uzantı varsayılan olarak etkinleştirilir.

> [!NOTE]
> **Uzantıları Yönet** aracı, VSIX paketinin bir parçası olarak yüklenmediği sürece uzantıya erişmek için kullanılamaz.

::: moniker-end

::: moniker range="vs-2017"

*.pkgdef* dosyaları aşağıdaki konumlardan birine yüklenmelidir:

- *%localappdata%\Microsoft\Visual Studio\15.0\Uzantılar\\*

- *%vsinstalldir%\Common7\IDE\Uzantılar\\*

Yükleme klasörü *%localappdata%\Microsoft\Visual Studio\15.0\Extensions\\*ise, uzantı Visual Studio tarafından tanınır, ancak varsayılan olarak devre dışı bırakılır. Kullanıcı **Uzantıları ve Güncelleştirmeleri**kullanarak uzantısı etkinleştirebilirsiniz.

Yükleme klasörü *%vsinstalldir%\Common7\IDE\Extensions\\*ise, uzantı varsayılan olarak etkinleştirilir.

> [!NOTE]
> **Uzantılar ve Güncelleştirmeler** aracı, VSIX paketinin bir parçası olarak yüklenmediği sürece uzantıya erişmek için kullanılamaz.

::: moniker-end

## <a name="see-also"></a>Ayrıca bkz.
- [CreateExpInstance yardımcı programı](../../extensibility/internals/createexpinstance-utility.md)

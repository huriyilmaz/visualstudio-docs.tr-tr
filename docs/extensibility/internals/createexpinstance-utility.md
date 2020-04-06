---
title: CreateExpInstance Programı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6a6b302976495e6067fad14317856cda4ac4625f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80709238"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance yardımcı programı
Visual Studio'nun deneysel bir örneğini oluşturmak, sıfırlamak veya silmek için **CreateExpInstance** yardımcı programını kullanın. Temel ürünü değiştirmeden Visual Studio uzantılarını hata ayıklamak ve test etmek için deneysel örneği kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametreler
 **/Oluştur** Deneysel örneği oluşturur.

 **/Sıfırlama** Deneme örneğini siler ve sonra yeni bir örnek oluşturur.

 **/Temiz** Deneme örneğini siler.

 **/VSInstance** Kopyalanması gereken temel Visual Studio örneğini içeren dizinin adı.

 **/RootSuffix** Deney örneği dizininin adını eklemek için sonek.

## <a name="remarks"></a>Açıklamalar
 Visual Studio uzantısı üzerinde çalışırken, varsayılan deneme örneğini açmak ve geçerli uzantıyı yüklemek için F5 tuşuna basabilirsiniz. Deneme örneği yoksa, Visual Studio varsayılan ayarlara sahip bir örnek oluşturur.

 Deneme örneğinin varsayılan konumu Visual Studio sürüm numarasına bağlıdır. Örneğin, Visual Studio 2015 için konum *\\%localappdata%\Microsoft\VisualStudio\14.0Exp'dir.* Dizin konumundaki tüm dosyalar bu örneğin bir parçası olarak kabul edilir. Dizin adı varsayılan konuma değiştirilmedikçe, ek deneysel örnekler Visual Studio tarafından yüklenmez.

 Visual Studio, deneme örneğini açtığında sistem kayıt defterine erişmez. Bu, kayıt kovanının deneysel bir sürümünü kullanan Visual Studio'nun önceki sürümlerinden farklıdır.

 **CreateExpInstance** yardımcı programı **VsRegEx** yardımcı programının yerini alır.

 Aşağıdaki örnek, Visual Studio'nun varsayılan deneysel örneğini sıfırlar:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)

---
title: CreateExpInstance yardımcı programı | Microsoft Docs
description: Visual Studio 'nun deneysel bir örneğini oluşturmanızı, sıfırlamayı veya silmenizi sağlayan CreateExpInstance yardımcı programı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: c02e85a96d59645787d3018100949369d52c8980
ms.sourcegitcommit: 2244665d5a0e22d12dd976417f2a782e68684705
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/28/2020
ms.locfileid: "96305360"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance yardımcı programı
Visual Studio 'nun deneysel bir örneğini oluşturmak, sıfırlamak veya silmek için **CreateExpInstance** yardımcı programını kullanın. Temel ürünü değiştirmeden Visual Studio uzantıları hatalarını ayıklamak ve test etmek için deneysel örneği kullanabilirsiniz.

## <a name="syntax"></a>Söz dizimi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametreler
 **/Create** Deneysel örneği oluşturur.

 **/Reset** Deneysel örneği siler ve yeni bir tane oluşturur.

 **/Clean** Deneysel örneği siler.

 **/Vsınstance** Kopyalanacak temel Visual Studio örneğini içeren dizinin adı.

 **/Rootsuffix** Deneysel örnek dizininin adına eklenecek sonek.

## <a name="remarks"></a>Açıklamalar
 Visual Studio uzantısı üzerinde çalışırken, F5 tuşuna basarak varsayılan Deneysel örneği açabilir ve geçerli uzantıyı yükleyebilirsiniz. Deneysel örnek yoksa, Visual Studio varsayılan ayarlara sahip bir tane oluşturur.

 Deneysel Örneğin varsayılan konumu, Visual Studio sürüm numarasına bağlıdır. Örneğin, Visual Studio 2015 için konum *%LocalAppData%\Microsoft\VisualStudio\14.0Exp \\*' dir. Dizin konumundaki tüm dosyalar, bu örneğin bir parçası olarak kabul edilir. Dizin adı varsayılan konum olarak değiştirilmediği takdirde, diğer deneysel örnekler Visual Studio tarafından yüklenmez.

 Visual Studio deneysel örneği açtığında sistem kayıt defterine erişemez. Bu, Visual Studio 'nun, kayıt defteri kovanının deneysel bir sürümünü kullanan önceki sürümlerinden farklıdır.

 **CreateExpInstance** yardımcı programı, **VsRegEx** yardımcı programının yerini alır.

 Aşağıdaki örnek, Visual Studio 'nun varsayılan Deneysel örneğini sıfırlar:

 **CreateExpInstance.exe/Reset/Vsınstance = 14.0/RootSuffix = exp**

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)

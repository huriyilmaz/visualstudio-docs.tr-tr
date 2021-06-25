---
title: CreateExpInstance yardımcı programı | Microsoft Docs
description: Visual Studio 'nun deneysel bir örneğini oluşturmanızı, sıfırlamayı veya silmenizi sağlayan CreateExpInstance yardımcı programı hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- experimental builds
- experimental hive
- experimental instance
- createexpinstance
- createexpinst
ms.assetid: 03779774-9401-49ae-997c-0c3ab25ed0d5
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: cce9bc25cb2ed820d3291ab65d94a868bb401ec9
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112898142"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance yardımcı programı
Visual Studio 'nun deneysel bir örneğini oluşturmak, sıfırlamak veya silmek için **CreateExpInstance** yardımcı programını kullanın. Temel ürünü değiştirmeden Visual Studio uzantıları hatalarını ayıklamak ve test etmek için deneysel örneği kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

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

---
title: CreateExpInstance Yardımcı Programı | Microsoft Docs
description: Deneysel bir örnek oluşturmanızı, sıfırlamanızı veya silmenizi sağlayan CreateExpInstance yardımcı programı hakkında Visual Studio.
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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: ee0c1daa8c56f759c39f4affb175b3894cbf9039
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126626169"
---
# <a name="createexpinstance-utility"></a>CreateExpInstance yardımcı programı
Deneysel bir örnek oluşturmak, sıfırlamak veya silmek için **CreateExpInstance** yardımcı programını Visual Studio. Temel alınan ürünü değiştirmeden uzantılarda hata ayıklamak Visual Studio test etmek için deneysel örneği kullanabilirsiniz.

## <a name="syntax"></a>Sözdizimi

```
CreateExpInstance.exe [/Create | /Reset | /Clean] /VSInstance=VsInstance /RootSuffix=Suffix
```

## <a name="parameters"></a>Parametreler
 **/Create** Deneysel örneği oluşturur.

 **/Reset** Deneysel örneği siler ve ardından yeni bir örnek oluşturur.

 **/Clean** Deneysel örneği siler.

 **/VSInstance** Kopyalanır temel örnek içeren Visual Studio adı.

 **/RootSuffix** Deneysel örnek dizininin adına eklenecek sonek.

## <a name="remarks"></a>Açıklamalar
 Bir uzantı üzerinde çalışırken Visual Studio F5 tuşuna basarak varsayılan deneysel örneği açabilir ve geçerli uzantıyı yükleyebilirsiniz. Deneysel örnek yoksa, Visual Studio ayarları olan bir örnek oluşturur.

 Deneysel örneğin varsayılan konumu, örnek sürüm numarasına Visual Studio bağlıdır. Örneğin, Visual Studio 2015 için konum *%localappdata%\Microsoft\VisualStudio\14.0Exp konumundadır. \\* Dizin konumdaki tüm dosyalar bu örneğin parçası olarak kabul edilir. Dizin adı varsayılan konuma değiştirilene Visual Studio ek deneysel örnekler bu örnek tarafından yüklenmez.

 Visual Studio, deneysel örneği açtığında sistem kayıt defterine erişmez. Bu, kayıt defteri kovanının deneysel Visual Studio kullanılan önceki Visual Studio sürümlerinden farklıdır.

 **CreateExpInstance** yardımcı **programı, VsRegEx yardımcı programını** değiştirir.

 Aşağıdaki örnek, varsayılan deneysel Visual Studio:

 **CreateExpInstance.exe /Reset /VSInstance=14.0 /RootSuffix=Exp**

## <a name="see-also"></a>Ayrıca bkz.
- [VSPackage’lar](../../extensibility/internals/vspackages.md)

---
title: -SafeMode (devenv.exe)
description: Visual Studio 'Yu güvenli modda başlatmak için SafeMode Devenv komut satırı anahtarını kullanarak yalnızca varsayılan ortam ve Hizmetleri yükleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /SafeMode Devenv switch
- Devenv, /SafeMode switch
- SafeMode switch
ms.assetid: b191f6a5-8f12-47ec-bcc7-b68149a22aa8
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1626776ec41bdbdfe5ad2b611516e62ada4f15a3
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99957874"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Visual Studio 'Yu güvenli modda başlatır, yalnızca varsayılan ortam ve Hizmetleri yükleyerek.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Açıklamalar

Bu anahtar, Visual Studio başlatıldığında tüm üçüncü taraf VSPackages 'nin yüklenmesini engeller ve kararlı yürütmeye izin verir.

## <a name="example"></a>Örnek

Aşağıdaki örnekte, Visual Studio güvenli modda başlatılır.

```shell
devenv /safemode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

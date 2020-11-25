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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4d8f663ca581892ba3207acbb0271586c322bad2
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039885"
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

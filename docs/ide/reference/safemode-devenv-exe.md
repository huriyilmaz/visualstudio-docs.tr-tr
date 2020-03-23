---
title: -SafeMode (devenv.exe)
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
ms.openlocfilehash: f180a45b274ec3042b7e150a43b5e8681fafcfed
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593596"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Visual Studio'yu güvenli modda başlatArak yalnızca varsayılan ortamı ve hizmetleri yükler.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Açıklamalar

Bu anahtar, Visual Studio başladığında tüm üçüncü taraf VSPackages'ın yüklenmesine engel olarak kararlı yürütmesağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio'yu güvenli modda başlatır.

```shell
devenv /safemode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

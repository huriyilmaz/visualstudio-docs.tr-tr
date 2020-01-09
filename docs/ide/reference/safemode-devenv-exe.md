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
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593596"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Visual Studio 'Yu güvenli modda başlatır, yalnızca varsayılan ortam ve Hizmetleri yükleyerek.

## <a name="syntax"></a>Sözdizimi

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

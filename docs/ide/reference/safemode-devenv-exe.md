---
title: -SafeMode (devenv.exe)
description: SafeMode devenv komut satırı anahtarını kullanarak yalnızca varsayılan ortamı ve Visual Studio modunda başlatmayı öğrenin.
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
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: abc61c4a92bfab394fab783196ff2ca9fab831d4
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627135"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Güvenli Visual Studio, yalnızca varsayılan ortam ve hizmetleri yükleniyor olarak başlatılır.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Açıklamalar

Bu anahtar, tüm üçüncü taraf VSPackage'ların Visual Studio ve kararlı yürütmeye olanak sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio modunda başlatılır.

```shell
devenv /safemode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

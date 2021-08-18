---
title: -SafeMode (devenv.exe)
description: SafeMode devenv komut satırı anahtarını kullanarak güvenli modda Visual Studio ortamı ve hizmetleri yükleme hakkında bilgi edinebilirsiniz.
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
ms.openlocfilehash: b89fe1bd998b8bd74ebb9e80998eac53824bceddebd9d8a208a038746cfa2daf
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121334256"
---
# <a name="safemode-devenvexe"></a>/SafeMode (devenv.exe)

Güvenli Visual Studio, yalnızca varsayılan ortam ve hizmetleri yükleniyor olarak başlatılır.

## <a name="syntax"></a>Syntax

```shell
devenv /SafeMode
```

## <a name="remarks"></a>Açıklamalar

Bu anahtar, uygulama başlatıldığında tüm üçüncü taraf VSPackage'ların yüklenmesini Visual Studio kararlı yürütmeye olanak sağlar.

## <a name="example"></a>Örnek

Aşağıdaki örnek, Visual Studio modunda çalışmaya başlar.

```shell
devenv /safemode
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

---
title: -DebugExe (devenv.exe)
description: Hata ayıklamak üzere belirtilen yürütülebilir dosyayı açmak için DebugExe devenv komut satırı anahtarını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
- debugging executables
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8c65427c3228697b4d9e0faa07943f6e5ba7cc29
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122117390"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Hata ayıklamak için belirtilen yürütülebilir dosyayı açar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Bağımsız değişkenler

- *Yürütülebilir Dosya*

  Gereklidir. Bir dosyanın yolu ve dosya `.exe` adı. Dosya bulunamıyorsa veya yoksa uyarı veya hata görüntülenmez ve `.exe` Visual Studio başlar.

## <a name="remarks"></a>Açıklamalar

*ExecutableFile* parametresini takip eden tüm dizeler bu dosyaya bağımsız değişken olarak geçirilsin.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hata ayıklama `MyApplication.exe` için dosyasını açar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

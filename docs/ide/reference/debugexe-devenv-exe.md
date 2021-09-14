---
title: -DebugExe (devenv.exe)
description: Hata ayıklama için belirtilen yürütülebilir dosyayı açmak üzere DebugExe Devenv komut satırı anahtarını nasıl kullanacağınızı öğrenin.
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
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634422"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Ayıklanmakta olan belirtilen yürütülebilir dosyayı açar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Bağımsız değişkenler

- *ExecutableFile*

  Gereklidir. Bir dosyanın yolu ve dosya adı `.exe` . `.exe`dosya bulunamazsa veya yoksa, uyarı veya hata gösterilmez ve Visual Studio normal olarak başlatılır.

## <a name="remarks"></a>Açıklamalar

*ExecutableFile* parametresini izleyen dizeler, bu dosyaya bağımsız değişken olarak geçirilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `MyApplication.exe` hata ayıklama için dosyasını açar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

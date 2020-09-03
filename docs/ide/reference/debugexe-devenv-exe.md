---
title: -DebugExe (devenv.exe)
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: aeae28288936b6723b53e826142a4888ad0bc8b4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75570147"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Ayıklanmakta olan belirtilen yürütülebilir dosyayı açar.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Bağımsız değişkenler

- *ExecutableFile*

  Gereklidir. Bir dosyanın yolu ve dosya adı `.exe` . `.exe`Dosya bulunamazsa veya yoksa, uyarı veya hata gösterilmez ve Visual Studio normal olarak başlatılır.

## <a name="remarks"></a>Açıklamalar

*ExecutableFile* parametresini izleyen dizeler, bu dosyaya bağımsız değişken olarak geçirilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, `MyApplication.exe` hata ayıklama için dosyasını açar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

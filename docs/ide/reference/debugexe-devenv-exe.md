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
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75570147"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Debugged olmak üzere belirtilen yürütülebilir dosyayı açar.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *ExecutableFile*

  Gereklidir. Bir `.exe` dosyanın yolu ve dosya adı. `.exe` Dosya bulunmazsa veya yoksa, hiçbir uyarı veya hata görüntülenmez ve Visual Studio normal olarak başlar.

## <a name="remarks"></a>Açıklamalar

*ExecutableFile* parametresini izleyen tüm dizeleri bağımsız değişken olarak bu dosyaya geçirilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hata `MyApplication.exe` ayıklama için dosyayı açar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

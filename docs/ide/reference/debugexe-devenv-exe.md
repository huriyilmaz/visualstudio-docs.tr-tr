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
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bb4eb1eb49cd6b29740fb6d365a98a51cc28387e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661674"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)

Ayıklanmakta olan belirtilen yürütülebilir dosyayı açar.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /DebugExe ExecutableFile
```

## <a name="arguments"></a>Arguments

- *ExecutableFile*

  Gerekli. @No__t_0 bir dosyanın yolu ve dosya adı. @No__t_0 dosyası bulunamazsa veya yoksa, uyarı veya hata gösterilmez ve Visual Studio normal olarak başlatılır.

## <a name="remarks"></a>Açıklamalar

*ExecutableFile* parametresini izleyen dizeler, bu dosyaya bağımsız değişken olarak geçirilir.

## <a name="example"></a>Örnek

Aşağıdaki örnek, hata ayıklama için `MyApplication.exe` dosyasını açar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
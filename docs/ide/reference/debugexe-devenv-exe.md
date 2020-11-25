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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6e60c3fb8a72caa44bcf70ac36850748ce240d42
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039477"
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

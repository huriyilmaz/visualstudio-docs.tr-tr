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
ms.openlocfilehash: 9a8ce446e110c8eebec6b9d10a91d6e7becb45a89e9912bfd98307d92ddb4459
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121429478"
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

Aşağıdaki örnek, hata ayıklama için `MyApplication.exe` dosyasını açar.

```shell
devenv /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)

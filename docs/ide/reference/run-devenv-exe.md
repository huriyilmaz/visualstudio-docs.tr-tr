---
title: -Run (devenv.exe)
description: Belirtilen proje veya çözümü derlemek ve çalıştırmak için devenv Run komut satırı anahtarını nasıl kullanacağınızı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- /Run Devenv
- Run Devenv switch
- applications [Visual Studio], running
- /R Devenv switch
- Devenv, /Run switch
- R Devenv switch (/R)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e523220ca3269b6af5404ce2d6ab653f29698599
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039912"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Belirtilen proje veya çözümü derler ve çalıştırır.

## <a name="syntax"></a>Söz dizimi

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Bir çözüm dosyasının tam yolu ve adı.

- *ProjectName*

  Bir proje dosyasının tam yolu ve adı.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Belirtilen proje veya çözümü, etkin çözüm yapılandırması için belirtilen ayarlara göre derler ve çalıştırır. Bu anahtar, IDE 'yi başlatır ve proje veya çözüm çalışmayı tamamladıktan sonra etkin bırakır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere Özet bilgiler, **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/Out` .

## <a name="example"></a>Örnek

Bu örnekte, `MySolution` etkin dağıtım yapılandırması kullanılarak çözüm çalıştırılır.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

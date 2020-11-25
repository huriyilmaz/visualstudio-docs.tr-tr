---
title: -RunExit (devenv.exe)
description: Belirtilen proje veya çözümü derlemek ve çalıştırmak için RunExit Devenv komut satırı anahtarını kullanmayı ve ardından IDE 'yi kapatmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 12/10/2018
ms.topic: reference
helpviewer_keywords:
- RunExit Devenv switch
- Devenv, /RunExit switch
- /RunExit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 2a1e0af28e8a96860039381b958d63e161a24936
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96039856"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Belirtilen proje veya çözümü derler ve çalıştırır ve ardından tümleşik geliştirme ortamını (IDE) kapatır.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Bir çözüm dosyasının tam yolu ve adı.

- *ProjectName*

  Bir proje dosyasının tam yolu ve adı.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Belirtilen proje veya çözümü, etkin çözüm yapılandırması için belirtilen ayarlara göre derler ve çalıştırır. Bu anahtar, proje veya çözüm çalıştırılırken IDE 'yi en aza indirir. Proje veya çözüm çalışmayı tamamladıktan sonra IDE 'yi kapatır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere Özet bilgiler, **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/Out` .

## <a name="example"></a>Örnek

Bu örnek, `MySolution` etkin dağıtım yapılandırmasını kullanarak çözümü küçültülmüş BIR IDE 'de çalıştırır ve ardından IDE 'yi kapatır.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

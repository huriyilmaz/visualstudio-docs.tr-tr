---
title: -RunExit (devenv.exe)
description: RunExit devenv komut satırı anahtarını kullanarak belirtilen projeyi veya çözümü derlemeyi ve çalıştırmayı ve ardından IDE'sini kapatmayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 67b53d02b53a49dd91b9c106537f9c6f342a947754e7bf138c7100cb4719aefb
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121400107"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Belirtilen projeyi veya çözümü derler ve çalıştırır ve ardından tümleşik geliştirme ortamını (IDE) kapatır.

## <a name="syntax"></a>Söz dizimi

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Çözüm dosyasının tam yolu ve adı.

- *Projeadı*

  Proje dosyasının tam yolu ve adı.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Etkin çözüm yapılandırması için belirtilen ayarlara göre belirtilen projeyi veya çözümü derler ve çalıştırır. Bu anahtar, proje veya çözüm çalışırken IDE'nin en aza indirilmesine neden olur. Proje veya çözüm çalışma tamamlandıktan sonra IDE'nin kapanması.

- Çift tırnak içinde boşluk içeren dizeleri içine alın.

- Hatalar da dahil olmak üzere özet bilgileri Komut penceresinde **veya** anahtarıyla belirtilen herhangi bir günlük dosyasında `/Out` görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, etkin dağıtım `MySolution` yapılandırmasını kullanarak çözümü simge durumuna küçültülmüş bir IDE'de çalıştırır ve ardından IDE'sini kapatır.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Run (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

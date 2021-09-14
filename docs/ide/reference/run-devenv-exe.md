---
title: -Run (devenv.exe)
description: Belirtilen projeyi veya çözümü derlemek ve çalıştırmak için Devenv çalıştır komut satırı anahtarını kullanmayı öğrenin.
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
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 7f3719ac3d0ff5f5a28a06ef25df1497e1c30d2b
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126627147"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)

Belirtilen projeyi veya çözümü derler ve çalıştırır.

## <a name="syntax"></a>Söz dizimi

```shell
devenv {/Run|/R} {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız değişkenler

- *SolutionName*

  Çözüm dosyasının tam yolu ve adı.

- *Projeadı*

  Proje dosyasının tam yolu ve adı.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıkışını göndermek istediğiniz dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Etkin çözüm yapılandırması için belirtilen ayarlara göre belirtilen projeyi veya çözümü derler ve çalıştırır. Bu anahtar IDE'nin başlatılmasını sağlar ve proje veya çözüm çalışma tamamlandıktan sonra etkin durumda bırakır.

- Çift tırnak içinde boşluk içeren dizeleri içine alın.

- Hatalar da dahil olmak üzere özet bilgileri Komut penceresinde **veya** anahtarıyla belirtilen herhangi bir günlük dosyasında `/Out` görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, etkin dağıtım `MySolution` yapılandırmasını kullanarak çözümü çalıştırır.

```shell
devenv /run "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md)
- [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

---
title: -RunExit (devenv.exe)
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
ms.openlocfilehash: 18ca581c5a8a7f631138e8b3eacff02a031e0931
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593609"
---
# <a name="runexit-devenvexe"></a>/RunExit (devenv.exe)

Belirtilen proje yi veya çözümü derler ve çalıştırır ve tümleşik geliştirme ortamını (IDE) kapatır.

## <a name="syntax"></a>Sözdizimi

```shell
devenv /RunExit {SolutionName|ProjectName} [/Out OutputFilename]
```

## <a name="arguments"></a>Bağımsız Değişkenler

- *SolutionName*

  Çözüm dosyasının tam yolu ve adı.

- *Projeadı*

  Proje dosyasının tam yolu ve adı.

- `/Out`*OutputFilename*

  İsteğe bağlı. Aracın çıktısını göndermek istediğiniz bir dosyanın adı. Dosya zaten varsa, araç çıktıyı dosyanın sonuna ekler.

## <a name="remarks"></a>Açıklamalar

Etkin çözüm yapılandırması için belirtilen ayarlara göre belirtilen projeyi veya çözümü derler ve çalıştırır. Bu anahtar, proje veya çözüm çalıştırılırken IDE'yi en aza indirir. Proje veya çözüm çalışma tamamlandıktan sonra IDE'yi kapatır.

- Çift tırnak işaretlerine boşluklar içeren dizeleri ekleyin.

- Hatalar da dahil olmak üzere özet bilgiler **Komut** penceresinde veya `/Out` anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek

Bu örnek, `MySolution` etkin dağıtım yapılandırmasını kullanarak çözümü simge durumuna küçültülmüş bir IDE'de çalıştırır ve ardından IDE'yi kapatır.

```
devenv /runexit "%USERPROFILE%\source\repos\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca bkz.

- [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md)
- [/Çalıştır (devenv.exe)](../../ide/reference/run-devenv-exe.md)
- [/Yapı (devenv.exe)](../../ide/reference/build-devenv-exe.md)
- [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md)
- [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

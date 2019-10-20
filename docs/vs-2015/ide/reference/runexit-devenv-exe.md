---
title: -Runexit (devenv. exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- runexit Devenv switch
- Devenv, /runexit switch
- /runexit Devenv switch
ms.assetid: bfc94875-5fc0-4110-b961-d59c0b403790
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6d1158a12de8b8adfe20fa6d045b756abf8d7b3c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72665492"
---
# <a name="runexit-devenvexe"></a>/Runexit (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen proje veya çözümü derler ve çalıştırır ve ardından tümleşik geliştirme ortamını (IDE) kapatır.

## <a name="syntax"></a>Sözdizimi

```
devenv /runexit {SolutionName|ProjectName}
```

## <a name="arguments"></a>Arguments
 `SolutionName` gerekiyor. Bir çözüm dosyasının tam yolu ve adı.

 `ProjectName` gerekiyor. Bir proje dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar
 Belirtilen proje veya çözümü, etkin çözüm yapılandırması için belirtilen ayarlara göre derler ve çalıştırır. Bu anahtar, proje veya çözüm çalıştırılırken IDE 'yi en aza indirir ve proje ya da çözümün çalışmasını tamamladıktan sonra IDE 'yi kapatır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere Özet bilgiler, **komut** penceresinde veya `/out` anahtarıyla belirtilen herhangi bir günlük dosyasında görüntülenebilir.

## <a name="example"></a>Örnek
 Bu örnek, etkin dağıtım yapılandırmasını kullanarak, simge durumuna küçültülmüş bir IDE 'de `MySolution` çözümünü çalıştırır ve ardından IDE 'yi kapatır.

```
devenv /runexit "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/Run (devenv. exe)](../../ide/reference/run-devenv-exe.md) [/Build (devenv. exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv. exe](../../ide/reference/rebuild-devenv-exe.md) ) [/Out (devenv. exe)](../../ide/reference/out-devenv-exe.md)

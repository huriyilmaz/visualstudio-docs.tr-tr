---
title: -Çalıştır (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- /run Devenv
- run Devenv switch
- applications [Visual Studio], running
- /r Devenv switch
- Devenv, /run switch
- r Devenv switch (/r)
ms.assetid: b1f22f9d-39a5-4918-8a2a-4b5c1e872665
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b2716995e8ff3a318262284b5733a471086c68c1
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72665517"
---
# <a name="run-devenvexe"></a>/Run (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Belirtilen proje veya çözümü derler ve çalıştırır.

## <a name="syntax"></a>Söz dizimi

```
devenv {/run|/r} {SolutionName|ProjectName}
```

## <a name="arguments"></a>Bağımsız değişkenler
 `SolutionName` Gerekli. Bir çözüm dosyasının tam yolu ve adı.

 `ProjectName` Gerekli. Bir proje dosyasının tam yolu ve adı.

## <a name="remarks"></a>Açıklamalar
 Belirtilen proje veya çözümü, etkin çözüm yapılandırması için belirtilen ayarlara göre derler ve çalıştırır. Bu anahtar, tümleşik geliştirme ortamını (IDE) başlatır ve proje veya çözümün çalışmasını tamamladıktan sonra etkin bırakır.

- Boşluk içeren dizeleri çift tırnak işaretleri içine alın.

- Hatalar da dahil olmak üzere Özet bilgiler, **komut** penceresinde veya anahtarla belirtilen herhangi bir günlük dosyasında görüntülenebilir `/out` .

## <a name="example"></a>Örnek
 Bu örnekte, `MySolution` etkin dağıtım yapılandırması kullanılarak çözüm çalıştırılır.

```
devenv /run "C:\Documents and Settings\someuser\My Documents\Visual Studio\Projects\MySolution\MySolution.sln"
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv komut satırı anahtarları](../../ide/reference/devenv-command-line-switches.md) [/runexit (devenv.exe)](../../ide/reference/runexit-devenv-exe.md) [/Build (devenv.exe)](../../ide/reference/build-devenv-exe.md) [/Rebuild (devenv.exe)](../../ide/reference/rebuild-devenv-exe.md) [/Out (devenv.exe)](../../ide/reference/out-devenv-exe.md)

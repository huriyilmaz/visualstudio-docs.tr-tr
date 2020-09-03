---
title: -DebugExe (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /DebugExe switch
- DebugExe switch
- /DebugExe [devenv.exe]
ms.assetid: cd700006-1648-418f-924b-4b1e5c1412ab
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f472add6b821693d1d48397e878db19e707e2868
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72660800"
---
# <a name="debugexe-devenvexe"></a>/DebugExe (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Ayıklanmakta olan belirtilen yürütülebilir dosyayı açar.

## <a name="syntax"></a>Söz dizimi

```
Devenv /debugexe ExecutableFile
```

## <a name="arguments"></a>Bağımsız değişkenler
 `ExecutableFile` Gerekli. Bir. exe dosyasının yolu ve dosya adı.

 . Exe dosyası bulunamazsa veya yoksa, hiçbir uyarı veya hata görüntülenmez ve [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] normal olarak başlatılır.

## <a name="remarks"></a>Açıklamalar
 Parametresini izleyen dizeler, `ExecutableFile` Bu dosyaya bağımsız değişken olarak geçirilir.

## <a name="example"></a>Örnek
 Aşağıdaki örnek, `MyApplication.exe` hata ayıklama için dosyasını açar.

```
Devenv.exe /debugexe MyApplication.exe
```

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)

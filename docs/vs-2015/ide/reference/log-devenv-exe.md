---
title: -Günlük (devenv.exe) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
helpviewer_keywords:
- Devenv, /Log switch
- Log switch [devenv.exe]
- /Log Devenv switch
ms.assetid: ae23c4ae-2376-4fe3-b8d2-81d34e61c8ba
caps.latest.revision: 13
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f427edfe294605b7b2adcbb0889e48c4f37b6ba9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72666840"
---
# <a name="log-devenvexe"></a>/Log (devenv.exe)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Tüm etkinliği, sorun giderme amacıyla günlük dosyasına kaydeder. Bu dosya, `devenv /log` en az bir kez çağrıldıktan sonra görüntülenir. Varsayılan olarak, günlük dosyası:

 *% AppData%* \Microsoft\visualstudio \\ *Sürüm*\ActivityLog.xml

 Burada *Sürüm* , Visual Studio sürümüdür. Ancak, farklı bir yol ve dosya adı belirtebilirsiniz.

## <a name="syntax"></a>Syntax

```
Devenv /log Path\NameOfLogFile
```

## <a name="remarks"></a>Açıklamalar
 Bu anahtar, diğer tüm anahtarlardan sonra komut satırının en sonunda görünmelidir.

 Günlük,/log anahtarıyla çağrınızda, Visual Studio 'nun tüm örnekleri için yazılır. Anahtar olmadan çağırılabilen Visual Studio örneklerini günlüğe kaydetmez.

## <a name="see-also"></a>Ayrıca Bkz.
 [Devenv Komut Satırı Anahtarları](../../ide/reference/devenv-command-line-switches.md)

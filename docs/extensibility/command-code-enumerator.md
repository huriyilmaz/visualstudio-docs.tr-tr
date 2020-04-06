---
title: Komut Kodu Kod Layıcı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 15916d26ac0120417205af0bb9117a45ec0397c6
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739793"
---
# <a name="command-code-enumerator"></a>Komut kodu tümumerator
Bu enumerator, [sccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md) ve [SccPopulateList](../extensibility/sccpopulatelist-function.md)seçeneklerinde seçeneklerin belirtildiği komutu belirtmek için kullanılır.

## <a name="syntax"></a>Sözdizimi

```
enum SCCCOMMAND {
   SCC_COMMAND_GET,
   SCC_COMMAND_CHECKOUT,
   SCC_COMMAND_CHECKIN,
   SCC_COMMAND_UNCHECKOUT,
   SCC_COMMAND_ADD,
   SCC_COMMAND_REMOVE,
   SCC_COMMAND_DIFF,
   SCC_COMMAND_HISTORY,
   SCC_COMMAND_RENAME,
   SCC_COMMAND_PROPERTIES,
   SCC_COMMAND_OPTIONS
};
```

## <a name="members"></a>Üyeler
SCC_COMMAND_GET [SccGet](../extensibility/sccget-function.md)karşılık gelir.

SCC_COMMAND_CHECKOUT [SccCheckout](../extensibility/scccheckout-function.md)karşılık gelir.

SCC_COMMAND_CHECKIN [SccCheckin](../extensibility/scccheckin-function.md)karşılık gelir.

SCC_COMMAND_UNCHECKOUT [SccUncheckout](../extensibility/sccuncheckout-function.md)karşılık gelir.

SCC_COMMAND_ADD [SCCAdd](../extensibility/sccadd-function.md)karşılık gelir.

SCC_COMMAND_REMOVE [SccRemove](../extensibility/sccremove-function.md)karşılık gelir.

SCC_COMMAND_DIFF [SccDiff](../extensibility/sccdiff-function.md)karşılık gelir.

SCC_COMMAND_HISTORY [SccHistory](../extensibility/scchistory-function.md)karşılık gelir.

SCC_COMMAND_RENAME [SccRename](../extensibility/sccrename-function.md)karşılık gelir.

SCC_COMMAND_PROPERTIES [SccProperties](../extensibility/sccproperties-function.md)karşılık gelir.

SCC_COMMAND_OPTIONS [SccSetOption](../extensibility/sccsetoption-function.md)karşılık gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)

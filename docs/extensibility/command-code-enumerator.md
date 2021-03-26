---
title: Komut kodu numaralandırıcısı | Microsoft Docs
description: Komut kodu numaralandırıcısı, seçeneklerin belirtilme komutunu göstermek için Sccgetcommandooptıons ve SccPopulateListto seçeneklerinde kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: e2df7ca11d5e93a3ae43d2a6bd1d7ccf8dfe5aa6
ms.sourcegitcommit: f2916d8fd296b92cc402597d1d1eecda4f6cccbf
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/25/2021
ms.locfileid: "105089712"
---
# <a name="command-code-enumerator"></a>Komut kodu numaralandırıcısı
Bu Numaralandırıcı, seçeneklerin belirtilme komutunu göstermek için [Sccgetcommandooptıons](../extensibility/sccgetcommandoptions-function.md) ve [SccPopulateList](../extensibility/sccpopulatelist-function.md)seçeneklerinde kullanılır.

## <a name="syntax"></a>Syntax

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
SCC_COMMAND_GET [SccGet](../extensibility/sccget-function.md)öğesine karşılık gelir.

SCC_COMMAND_CHECKOUT [SccCheckout](../extensibility/scccheckout-function.md)'A karşılık gelir.

SCC_COMMAND_CHECKIN [SccCheckin](../extensibility/scccheckin-function.md)öğesine karşılık gelir.

SCC_COMMAND_UNCHECKOUT, [SccUncheckout](../extensibility/sccuncheckout-function.md)öğesine karşılık gelir.

SCC_COMMAND_ADD, [SccAdd](../extensibility/sccadd-function.md)'ye karşılık gelir.

SCC_COMMAND_REMOVE [SccRemove](../extensibility/sccremove-function.md)öğesine karşılık gelir.

SCC_COMMAND_DIFF [SccDiff](../extensibility/sccdiff-function.md)öğesine karşılık gelir.

SCC_COMMAND_HISTORY, [SccHistory](../extensibility/scchistory-function.md)karşılık gelir.

SCC_COMMAND_RENAME [SccRename](../extensibility/sccrename-function.md)öğesine karşılık gelir.

SCC_COMMAND_PROPERTIES [Sccözelliklerine](../extensibility/sccproperties-function.md)karşılık gelir.

SCC_COMMAND_OPTIONS [SccSetOption](../extensibility/sccsetoption-function.md)öğesine karşılık gelir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [SccGetCommandOptions](../extensibility/sccgetcommandoptions-function.md)
- [SccPopulateList](../extensibility/sccpopulatelist-function.md)

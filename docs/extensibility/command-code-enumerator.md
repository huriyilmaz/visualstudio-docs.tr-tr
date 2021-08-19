---
title: Komut kodu numaralandırıcısı | Microsoft Docs
description: Komut kodu numaralandırıcısı, seçeneklerin belirtilme komutunu göstermek için Sccgetcommandooptıons ve SccPopulateListto seçeneklerinde kullanılır.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 153b39b1742dc6f78e23df1f1cdd30b052738684
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122133308"
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

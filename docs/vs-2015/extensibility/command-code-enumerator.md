---
title: Komut kodu numaralandırıcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command code enumerator
- source control plug-ins, command code enumeration
ms.assetid: 5d2c360c-59e4-4da8-bcb4-dd07c7441e40
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 06f1a3f7146125e59d02efc72a4d4fc9ab33be39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68184383"
---
# <a name="command-code-enumerator"></a>Komut Kodu Numaralandırıcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

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
 SCC_COMMAND_GET  
 [SccGet](../extensibility/sccget-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_CHECKOUT  
 [SccCheckout](../extensibility/scccheckout-function.md)'a karşılık gelir.  
  
 SCC_COMMAND_CHECKIN  
 [SccCheckin](../extensibility/scccheckin-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_UNCHECKOUT  
 [SccUncheckout](../extensibility/sccuncheckout-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_ADD  
 [SccAdd](../extensibility/sccadd-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_REMOVE  
 [SccRemove](../extensibility/sccremove-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_DIFF  
 [SccDiff](../extensibility/sccdiff-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_HISTORY  
 [SccHistory](../extensibility/scchistory-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_RENAME  
 [SccRename](../extensibility/sccrename-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_PROPERTIES  
 [SccProperties](../extensibility/sccproperties-function.md)öğesine karşılık gelir.  
  
 SCC_COMMAND_OPTIONS  
 [SccSetOption](../extensibility/sccsetoption-function.md)öğesine karşılık gelir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [Sccgetcommandoseçenekler](../extensibility/sccgetcommandoptions-function.md)   
 [SccPopulateList](../extensibility/sccpopulatelist-function.md)

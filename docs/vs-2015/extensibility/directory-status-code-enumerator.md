---
title: Dizin durum kodu numaralandırıcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e082a691a389d5cb9a8fa307a627b11911e0db78
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68185248"
---
# <a name="directory-status-code-enumerator"></a>Dizin Durumu Kod Numaralandırıcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccDirStatus`Numaralandırıcı, kaynak denetim sistemindeki bir dizinin durumunu belirten adlandırılmış sabit değerler içeriyor. Bu numaralandırma, [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)tarafından kullanılır. Bu, kaynak denetimi eklentisi API 'sinin sürüm 1,2 ' de kullanıma sunulmuştur.  
  
## <a name="syntax"></a>Syntax  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Üyeler  
 SCC_DIRSTATUS_INVALID  
 Durum alınamadı; Bu uygulamayı kullanmayın.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Dizin, kaynak denetimi altında değil.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Dizin, kaynak denetimi altında.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Bu dizine karşılık gelen proje boş.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

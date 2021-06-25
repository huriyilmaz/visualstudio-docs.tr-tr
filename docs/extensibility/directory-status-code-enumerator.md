---
title: Dizin durum kodu numaralandırıcısı | Microsoft Docs
description: SccDirStatus numaralandırıcısı, kaynak denetim sistemindeki bir dizinin durumunu belirten ve SccDirQueryInfo tarafından kullanılan adlandırılmış sabit değerleri içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: a504c6c080c34b4506cf4078b64465a3bd6c7d97
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112904236"
---
# <a name="directory-status-code-enumerator"></a>Dizin durumu kod numaralandırıcısı
`SccDirStatus`Numaralandırıcı, kaynak denetim sistemindeki bir dizinin durumunu belirten adlandırılmış sabit değerler içeriyor. Bu numaralandırma, [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)tarafından kullanılır. Bu, kaynak denetimi eklentisi API 'sinin sürüm 1,2 ' de kullanıma sunulmuştur.

## <a name="syntax"></a>Syntax

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Üyeler
 SCC_DIRSTATUS_INVALID durumu alınamadı; Bu uygulamayı kullanmayın.

 SCC_DIRSTATUS_NOTCONTROLLED Dizin, kaynak denetimi altında değil.

 SCC_DIRSTATUS_CONTROLLED Dizin, kaynak denetimi altında.

 Bu dizine karşılık gelen SCC_DIRSTATUS_EMPTYPROJ proje boş.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

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
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 81f7e81ded2b45b560350c065e13ef69455468d9
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126726950"
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

 bu dizine karşılık gelen SCC_DIRSTATUS_EMPTYPROJ Project boş.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

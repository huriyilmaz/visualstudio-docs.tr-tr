---
title: Dizin Durum Kodu KodLayıcı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7b5ebf61f2baa6e4277e27cd3c4d18a51e64f835
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712151"
---
# <a name="directory-status-code-enumerator"></a>Dizin durum kodu sayısallaştırıcı
Yerumerator kaynak `SccDirStatus` denetim sisteminde bir dizinin durumunu belirten adlı sabit değerler içerir. Bu numaralandırma [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)tarafından kullanılır. Bu, Kaynak Denetimi Eklentisi API sürümü 1.2 tanıtıldı.

## <a name="syntax"></a>Sözdizimi

```
enum SccDirStatus {
   SCC_DIRSTATUS_INVALID       = -1L,
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L
};
```

## <a name="members"></a>Üyeler
 SCC_DIRSTATUS_INVALID Durum elde edilemedi; buna güvenmeyin.

 SCC_DIRSTATUS_NOTCONTROLLED Dizini kaynak denetimi altında değildir.

 SCC_DIRSTATUS_CONTROLLED Directory kaynak kontrolü altındadır.

 bu dizine karşılık gelen SCC_DIRSTATUS_EMPTYPROJ Projesi boştur.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)

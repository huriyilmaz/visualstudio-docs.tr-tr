---
title: Dosya Durum Kodu Numaralayıcı | Microsoft Docs
description: SccStatus numaralayıcı, kaynak denetim sisteminde bir dosyanın durumunu belirten ve SccQueryInfo ile POPLISTFUNC tarafından kullanılan sabit değerler içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-sdk
ms.workload:
- vssdk
ms.openlocfilehash: 2e5014f3ba96d11fc5a851e5255404fae50289322062786a6952bf4bec192cb9
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121448331"
---
# <a name="file-status-code-enumerator"></a>Dosya durumu kodu numaralayıcı
`SccStatus`Numaralayıcı, kaynak denetim sisteminde bir dosyanın durumunu belirten adlandırılmış sabit değerler içerir. Bu numaralama [SccQueryInfo](../extensibility/sccqueryinfo-function.md) ve geri çağırma işlevi tarafından kullanılır (ayrıntılar için `POPLISTFUNC` bkz. [POPLISTFUNC).](../extensibility/poplistfunc.md)

## <a name="syntax"></a>Syntax

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Üyeler
 SCC_STATUS_INVALID Durumu alınamadı; buna güvenmez.

 SCC_STATUS_NOTCONTROLLED Dosyası kaynak denetimi altında değil.

 SCC_STATUS_CONTROLLED Dosya kaynak denetimi altında.

 SCC_STATUS_CHECKEDOUT yerel diskte geçerli kullanıcı tarafından kullanıma alınmış.

 SCC_STATUS_OUTOTHER Dosyası başka bir kullanıcı tarafından kullanıma alınmış.

 SCC_STATUS_OUTEXCLUSIVE dosyası özel olarak kullanıma alınmış.

 SCC_STATUS_OUTMULTIPLE Dosya birden fazla kullanıcı tarafından kullanıma alınmış.

 SCC_STATUS_OUTOFDATE Dosya en son değildir.

 SCC_STATUS_DELETED Dosya projeden silindi.

 SCC_STATUS_LOCKED dosyası kilitli; daha fazla sürüme izin verilmez.

 SCC_STATUS_MERGED dosya birleştirildi ama henüz düzeltildi/doğrulanmadı.

 SCC_STATUS_SHARED dosya projeler arasında paylaşılır.

 SCC_STATUS_PINNED dosyası açık bir sürümle paylaşılır.

 SCC_STATUS_MODIFIED Dosya değiştirildi/bozuk/ihlal edildi.

 SCC_STATUS_OUTBYUSER dosyası geçerli kullanıcı tarafından kullanıma alınmış.

 SCC_STATUS_NOMERGE dosya hiçbir zaman ile birleştirilemez ve GET öncesinde kaydedilemez.

 SCC_STATUS_RESERVED_1 kullanım için ayrılmıştır.

 SCC_STATUS_RESERVED_2 kullanım için ayrılmıştır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)

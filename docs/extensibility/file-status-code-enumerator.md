---
title: Dosya durum kodu numaralandırıcısı | Microsoft Docs
description: SccStatus numaralandırıcısı, kaynak denetim sistemindeki bir dosyanın durumunu belirten ve SccQueryInfo ve POPLISTFUNC tarafından kullanılan sabit değerleri içerir.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 0093e3a79a5a9caf9846c4b418226568e37828f0
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96994491"
---
# <a name="file-status-code-enumerator"></a>Dosya durum kodu numaralandırıcısı
`SccStatus`Numaralandırıcı, kaynak denetim sistemindeki bir dosyanın durumunu belirten adlandırılmış sabit değerler içeriyor. Bu numaralandırma, [SccQueryInfo](../extensibility/sccqueryinfo-function.md) ve callback işlevi tarafından kullanılır `POPLISTFUNC` (Ayrıntılar Için bkz. [poplistfunc](../extensibility/poplistfunc.md) ).

## <a name="syntax"></a>Sözdizimi

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
 SCC_STATUS_INVALID durumu alınamadı; Bu uygulamayı kullanmayın.

 SCC_STATUS_NOTCONTROLLED dosya kaynak denetimi altında değil.

 SCC_STATUS_CONTROLLED dosya kaynak denetimi altında.

 SCC_STATUS_CHECKEDOUT yerel diskteki geçerli kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_OUTOTHER dosya başka bir kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_OUTEXCLUSIVE dosya özel olarak kullanıma alındı.

 SCC_STATUS_OUTMULTIPLE dosya birden fazla kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_OUTOFDATE dosya en güncel değil.

 SCC_STATUS_DELETED dosya projeden silindi.

 SCC_STATUS_LOCKED dosya kilitli; daha fazla sürüm izni yok.

 SCC_STATUS_MERGED dosya birleştirildi ancak henüz düzeltilmedi/doğrulanmadı.

 SCC_STATUS_SHARED dosya projeler arasında paylaşılır.

 SCC_STATUS_PINNED dosya açık bir sürümle paylaşılıyor.

 SCC_STATUS_MODIFIED Dosya değiştirilmiş/bozuk/ihlal edildi.

 SCC_STATUS_OUTBYUSER dosya geçerli kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_NOMERGE dosya hiçbir şekilde birleştirilemez ve bir GET öncesinde kaydedilmemelidir.

 SCC_STATUS_RESERVED_1 iç kullanım için ayrılmıştır.

 SCC_STATUS_RESERVED_2 iç kullanım için ayrılmıştır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)

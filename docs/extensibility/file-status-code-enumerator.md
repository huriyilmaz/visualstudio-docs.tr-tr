---
title: Dosya Durum Kodu KodLayıcı | Microsoft Dokümanlar
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
ms.openlocfilehash: 184c8686ea184aea2cbd0a64873718cbe72f7615
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711447"
---
# <a name="file-status-code-enumerator"></a>Dosya durum kodu sayısallaştırıcı
Yerumerator `SccStatus` kaynak denetim sisteminde bir dosyanın durumunu belirten adlı sabit değerler içerir. Bu numaralandırma [SccQueryInfo](../extensibility/sccqueryinfo-function.md) ve `POPLISTFUNC` geri arama işlevi tarafından kullanılır (ayrıntılar için [POPLISTFUNC'a](../extensibility/poplistfunc.md) bakın).

## <a name="syntax"></a>Sözdizimi

```
enum SccStatus {
   SCC_STATUS_INVALID          = -1L,
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,
   SCC_STATUS_CONTROLLED       = 0x0001L,
   SCC_STATUS_CHECKEDOUT       = 0x0002L,
   SCC_STATUS_OUTOTHER         = 0x0004L,
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,
   SCC_STATUS_OUTOFDATE        = 0x0020L,
   SCC_STATUS_DELETED          = 0x0040L,
   SCC_STATUS_LOCKED           = 0x0080L,
   SCC_STATUS_MERGED           = 0x0100L,
   SCC_STATUS_SHARED           = 0x0200L,
   SCC_STATUS_PINNED           = 0x0400L,
   SCC_STATUS_MODIFIED         = 0x0800L,
   SCC_STATUS_OUTBYUSER        = 0x1000L
   SCC_STATUS_NOMERGE          = 0x2000L
   SCC_STATUS_RESERVED_1       = 0x4000L
   SCC_STATUS_RESERVED_2       = 0x8000L
};
```

## <a name="members"></a>Üyeler
 SCC_STATUS_INVALID Durum elde edilemedi; buna güvenmeyin.

 SCC_STATUS_NOTCONTROLLED Dosya kaynak denetimi altında değildir.

 SCC_STATUS_CONTROLLED Dosya kaynak denetimi altındadır.

 SCC_STATUS_CHECKEDOUT Yerel diskte geçerli kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_OUTOTHER Dosyası başka bir kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_OUTEXCLUSIVE Dosyası yalnızca kullanıma alındı.

 SCC_STATUS_OUTMULTIPLE Dosyası birden fazla kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_OUTOFDATE Dosya en son değil.

 SCC_STATUS_DELETED Dosyası projeden silindi.

 SCC_STATUS_LOCKED Dosya kilitli; başka sürümizin verilmemektedir.

 SCC_STATUS_MERGED Dosyası birleştirilmiştir, ancak henüz düzeltilmedi/doğrulanmadı.

 SCC_STATUS_SHARED Dosyası projeler arasında paylaşılır.

 SCC_STATUS_PINNED Dosya açık bir sürümle paylaşılır.

 SCC_STATUS_MODIFIED Dosyası değiştirildi/kırıldı/ihlal edildi.

 SCC_STATUS_OUTBYUSER Dosya geçerli kullanıcı tarafından kullanıma alındı.

 SCC_STATUS_NOMERGE Dosyası hiçbir zaman birleştirilebilir ve GET'den önce kaydedilmesi gerekmez.

 SCC_STATUS_RESERVED_1 dahili kullanım için ayrılmıştır.

 SCC_STATUS_RESERVED_2 dahili kullanım için ayrılmıştır.

## <a name="see-also"></a>Ayrıca bkz.
- [Kaynak kontrol eklentileri](../extensibility/source-control-plug-ins.md)
- [SccQueryInfo](../extensibility/sccqueryinfo-function.md)
- [POPLISTFUNC](../extensibility/poplistfunc.md)

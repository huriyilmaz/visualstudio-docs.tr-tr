---
title: Dosya durum kodu numaralandırıcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- named constants, SccStatus enumerator
- source control plug-ins, file status enumeration
- SccStatus enumerator
- file status code enumerator
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 16
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 1b6e74caa9eedd42e25339d62f5837ccfe82d001
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68204372"
---
# <a name="file-status-code-enumerator"></a>Dosya Durumu Kod Numaralandırıcısı
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

`SccStatus`Numaralandırıcı, kaynak denetim sistemindeki bir dosyanın durumunu belirten adlandırılmış sabit değerler içeriyor. Bu numaralandırma, [SccQueryInfo](../extensibility/sccqueryinfo-function.md) ve callback işlevi tarafından kullanılır `POPLISTFUNC` (Ayrıntılar Için bkz. [poplistfunc](../extensibility/poplistfunc.md) ).  
  
## <a name="syntax"></a>Syntax  
  
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
 SCC_STATUS_INVALID  
 Durum alınamadı; Bu uygulamayı kullanmayın.  
  
 SCC_STATUS_NOTCONTROLLED  
 Dosya kaynak denetimi altında değil.  
  
 SCC_STATUS_CONTROLLED  
 Dosya kaynak denetimi altında.  
  
 SCC_STATUS_CHECKEDOUT  
 Yerel diskte geçerli kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_OUTOTHER  
 Dosya başka bir kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_OUTEXCLUSIVE  
 Dosya özel olarak kullanıma alındı.  
  
 SCC_STATUS_OUTMULTIPLE  
 Dosya birden fazla kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_OUTOFDATE  
 Dosya en güncel değil.  
  
 SCC_STATUS_DELETED  
 Dosya projeden silindi.  
  
 SCC_STATUS_LOCKED  
 Dosya kilitli; daha fazla sürüm izni yok.  
  
 SCC_STATUS_MERGED  
 Dosya birleştirildi ancak henüz düzeltilmedi/doğrulanmadı.  
  
 SCC_STATUS_SHARED  
 Dosya projeler arasında paylaşılıyor.  
  
 SCC_STATUS_PINNED  
 Dosya açık bir sürümle paylaşılıyor.  
  
 SCC_STATUS_MODIFIED  
 Dosya değiştirilmiş/bozuk/ihlal edildi.  
  
 SCC_STATUS_OUTBYUSER  
 Dosya geçerli kullanıcı tarafından kullanıma alındı.  
  
 SCC_STATUS_NOMERGE  
 Dosya hiçbir şekilde birleştirilemez ve bir GET öncesinde kaydedilmemelidir.  
  
 SCC_STATUS_RESERVED_1  
 Dahili kullanım için ayrılmıştır.  
  
 SCC_STATUS_RESERVED_2  
 Dahili kullanım için ayrılmıştır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Kaynak denetimi eklentileri](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)

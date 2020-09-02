---
title: 'IDiaEnumDebugStreamData:: Next | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumDebugStreamData::Next method
ms.assetid: 114171dd-38fd-4bd7-a702-8ff887ffc99b
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4bdbf58321426890bffd45a08818dc5341bdfc3d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187392"
---
# <a name="idiaenumdebugstreamdatanext"></a>IDiaEnumDebugStreamData::Next
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Numaralandırılmış dizide belirtilen sayıda kaydı alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Next (   
   ULONG  celt,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[],  
   ULONG* pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 celt  
 'ndaki Alınacak kayıt sayısı.  
  
 cbData  
 'ndaki Veri arabelleğinin bayt cinsinden boyutu.  
  
 pcbData  
 dışı Döndürülen bayt sayısını döndürür. `data`Null ise, `pcbData` Tüm istenen kayıtlar için kullanılabilir olan toplam veri baytı sayısını içerir.  
  
 veri []  
 dışı Hata ayıklama akışı kayıt verileriyle doldurulacak bir arabellek.  
  
 Pceltfettiz  
 [in, out] İçindeki kayıt sayısını döndürür `data` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Daha fazla kayıt yoksa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaEnumDebugStreamData](../../debugger/debug-interface-access/idiaenumdebugstreamdata.md)   
 [IDiaEnumDebugStreams::Next](../../debugger/debug-interface-access/idiaenumdebugstreams-next.md)

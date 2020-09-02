---
title: 'IDiaStackWalkFrame:: readMemory | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaStackWalkFrame::readMemory method
ms.assetid: 7ab0b525-a5a7-4692-acad-e8c00fa9ab9a
caps.latest.revision: 15
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 97a868973d2a514150b8d728e685523e918f88f4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68150169"
---
# <a name="idiastackwalkframereadmemory"></a>IDiaStackWalkFrame::readMemory
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Görüntüden belleği okur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT readMemory (   
   MemoryTypeEnum type,  
   ULONGLONG va,  
   DWORD     cbData,  
   DWORD*    pcbData,  
   BYTE      data[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `type`  
 'ndaki Erişim için bellek türünü belirten [MemoryTypeEnum sabit](../../debugger/debug-interface-access/memorytypeenum.md) listesi değerlerinden biri.  
  
 `va`  
 'ndaki Okumaya başlamak için görüntüdeki sanal adres konumu.  
  
 `cbData`  
 'ndaki Veri arabelleğinin bayt cinsinden boyutu.  
  
 `pcbData`  
 dışı Döndürülen bayt sayısını döndürür. `data`İse `NULL` , `pcbData` kullanılabilir verilerin toplam bayt sayısını içerir.  
  
 `data`  
 dışı Belirtilen konumdan alınan verilerle doldurulacak bir arabellek.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaStackWalkFrame](../../debugger/debug-interface-access/idiastackwalkframe.md)

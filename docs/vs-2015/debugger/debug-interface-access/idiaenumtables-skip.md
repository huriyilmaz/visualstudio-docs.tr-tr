---
title: 'IDiaEnumTables:: Skip | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumTables::Skip method
ms.assetid: 5c9db956-0654-4f1a-8775-530aa980d8ec
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4498789b3497ea70faf9948fcf0d03c6196f250e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68161450"
---
# <a name="idiaenumtablesskip"></a>IDiaEnumTables::Skip
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Sabit Listesi dizisinde belirtilen sayıda tabloyu atlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Skip (   
   ULONG celt  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `celt`  
 'ndaki Atlanacak numaralandırma dizisindeki tablo sayısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, öğesini döndürür `S_OK` ; Aksi takdirde, atlanacak tablo yoksa, döndürür `S_FALSE` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaEnumTables](../../debugger/debug-interface-access/idiaenumtables.md)

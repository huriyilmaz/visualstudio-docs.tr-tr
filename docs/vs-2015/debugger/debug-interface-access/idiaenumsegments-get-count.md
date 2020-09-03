---
title: 'IDiaEnumSegments:: get_Count | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaEnumSegments::get_Count method
ms.assetid: c62a0fda-17b8-4cf6-b321-6014ce581096
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 445049452a91351ffff0cc18daa328777ed89dc9
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68189916"
---
# <a name="idiaenumsegmentsget_count"></a>IDiaEnumSegments::get_Count
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Segmentlerin sayısını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_Count (   
   LONG* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 pRetVal  
 [Out, retval] Parçaların sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaEnumSegments](../../debugger/debug-interface-access/idiaenumsegments.md)   
 [IDiaEnumSegments::Item](../../debugger/debug-interface-access/idiaenumsegments-item.md)

---
title: 'Idiareadexeatrboş Allback:: ReadExecutableAtRVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaReadExeAtRVACallback::ReadExecutableAtRVA method
ms.assetid: 3c1e965f-8f05-41a8-86d8-01830b2377c9
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 8d74543b7b57d188712c04bc43429357a5140c9e
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68187272"
---
# <a name="idiareadexeatrvacallbackreadexecutableatrva"></a>IDiaReadExeAtRVACallback::ReadExecutableAtRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Yürütülebilir dosyadan belirtilen göreli sanal adresten (RVA) başlayarak belirtilen bayt sayısını okur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT ReadExecutableAtRVA (   
   DWORD  relativeVirtualAddress,  
   DWORD  cbData,  
   DWORD* pcbData,  
   BYTE   data[]  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `relativeVirtualAddress`  
 'ndaki Okumaya başlamak için çalıştırılabilir dosyadaki RVA.  
  
 `cbData`  
 'ndaki Okunacak bayt sayısı.  
  
 `pcbData`  
 dışı Okunan bayt sayısını döndürür.  
  
 `data[]`  
 [in, out] Dosyadan okunan bayt ile doldurulmuş bir dizi.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, bir sanal adresi kullanarak bir yürütülebilir dosyadan veri baytları yüklemek için ÇYA destek kodu tarafından çağırılır. Bu yöntem, [IDiaDataSource:: loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md) metodunu desteklemek için çağrılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaReadExeAtRVACallback](../../debugger/debug-interface-access/idiareadexeatrvacallback.md)   
 [IDiaDataSource::loadDataForExe](../../debugger/debug-interface-access/idiadatasource-loaddataforexe.md)

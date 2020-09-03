---
title: 'IDiaSectionContrib:: get_nopad | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_nopad method
ms.assetid: f5c08603-0b3e-4e81-acf1-1b95a6a83bed
caps.latest.revision: 9
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 3044deb31214aae9c37ef7bb1f84324857ffb7d0
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151901"
---
# <a name="idiasectioncontribget_nopad"></a>IDiaSectionContrib::get_nopad
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bölümün bir sonraki bellek sınırına geçirilip geçirilmeyeceğini belirten bir bayrak alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_nopad(  
   BOOL* pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı `TRUE` Bölüm bir sonraki bellek sınırına dönmemelidir; Aksi takdirde döndürür `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` . `S_FALSE`Bu özellik desteklenmiyorsa döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu, genellikle yalnızca eski dosyalarda görülen bir özelliktir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

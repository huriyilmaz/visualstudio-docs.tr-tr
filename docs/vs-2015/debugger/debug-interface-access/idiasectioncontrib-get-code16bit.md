---
title: 'IDiaSectionContrib:: get_code16bit | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSectionContrib::get_code16bit method
ms.assetid: 8cde8fc5-9546-4f82-b4a8-afd0d835039e
caps.latest.revision: 10
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1aceb4956b7ce2517087511676ebeff2b061b673
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62576994"
---
# <a name="idiasectioncontribget_code16bit"></a>IDiaSectionContrib::get_code16bit
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bölümün 16 bit kod içerip içermediğini gösteren bir bayrak alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_code16bit(  
   BOOL *pRetVal  
};  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı `TRUE` Bölümdeki kodun 16 bit olup olmadığını döndürür; Aksi takdirde, döndürür `FALSE` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem yalnızca kodun 16 bit olduğunu gösterir. Kod 16 bit değilse, 32 bit veya 64 bit kod gibi başka bir şey olabilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSectionContrib](../../debugger/debug-interface-access/idiasectioncontrib.md)

---
title: 'IDiaSymbol:: get_baseSymbol | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: cabb5a18-bda7-47e8-9e46-5f4718579fc9
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9458f4e848f750d4a7eb11a866a2730f331e7244
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149804"
---
# <a name="idiasymbolget_basesymbol"></a>IDiaSymbol::get_baseSymbol
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

İşaretçinin dayandığı simgeyi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT get_baseSymbol(   
   IDiaSymbol** pRetVal);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı İşaretçinin temel aldığı simgenin işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)

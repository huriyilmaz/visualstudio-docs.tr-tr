---
title: 'IDiaSymbol:: get_oemSymbolId | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSymbol::get_oemSymbolId method
ms.assetid: 187801f0-bd82-4c5b-9fae-8eeb1a4ac0ce
caps.latest.revision: 11
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 4031672840237b0496ba7c6dbb9bb3b1658d7023
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64837915"
---
# <a name="idiasymbolget_oemsymbolid"></a>IDiaSymbol::get_oemSymbolId
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Özgün ekipman üreticisi (OEM) sembolünün KIMLIK değerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT get_oemSymbolId (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pRetVal`  
 dışı OEM 'nin dahili olarak atanmış sembol KIMLIĞINI döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
> [!NOTE]
> Dönüş değeri, `S_FALSE` özelliğin sembol için kullanılamadığı anlamına gelir.  
  
## <a name="remarks"></a>Açıklamalar  
 Tanımlayıcı, tüm sembolleri benzersiz olarak işaretlemek için DIA SDK tarafından oluşturulan benzersiz bir değerdir.  
  
 Bu özellik yalnızca [SymTagEnum numaralandırma](../../debugger/debug-interface-access/symtagenum.md) türüne sahip semboller için geçerlidir `SymTagCustomType` .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)

---
title: 'IDiaSession:: Findınlineframesbyrva | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: ddb3ff0e-cb3d-4fa0-af56-f064b218b264
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 1cb783936579eb3cd3c4903653ef6ad04e1bc381
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68151719"
---
# <a name="idiasessionfindinlineframesbyrva"></a>IDiaSession::findInlineFramesByRVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir istemcinin belirtilen göreli sanal adreste (RVA) bulunan tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT findInlineFramesByRVA (   
   IDiaSymbol*       parent,   DWORD             rva,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki `IDiaSymbol` Üst öğeyi temsil eden nesne.  
  
 `rva`  
 'ndaki Adresi RVA olarak belirtir.  
  
 `ppResult`  
 dışı `IDiaEnumSymbols` Alınan çerçevelerin listesini içeren bir nesnesi tutar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum numaralandırması](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)

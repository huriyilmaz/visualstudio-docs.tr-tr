---
title: 'IDiaSession:: findInlineFramesByVA | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 09551b40bde30d334706e728217ec6fcde9dfeb4
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68165552"
---
# <a name="idiasessionfindinlineframesbyva"></a>IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir istemcinin belirtilen bir sanal adresteki (VA) tüm satır içi çerçevelerde yineleme yapmasına izin veren bir sabit listesi alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `parent`  
 'ndaki `IDiaSymbol` Üst öğeyi temsil eden nesne.  
  
 `va`  
 'ndaki Adresi bir VA olarak belirtir.  
  
 `ppResult`  
 dışı `IDiaEnumSymbols` Alınan çerçevelerin listesini içeren bir nesnesi tutar.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [SymTagEnum Numaralandırması](../../debugger/debug-interface-access/symtagenum.md)

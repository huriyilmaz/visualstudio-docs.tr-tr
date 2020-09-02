---
title: IDiaSession::p ut_loadAddress | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaSession::put_loadAddress method
ms.assetid: b157b245-1ea0-4b80-8962-d8b278dbc742
caps.latest.revision: 14
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f697384874726904960fc5ba04733c3acfe1cd06
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64778226"
---
# <a name="idiasessionput_loadaddress"></a>IDiaSession::put_loadAddress
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu sembol deposundaki simgelere karşılık gelen yürütülebilir dosyanın yükleme adresini ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT put_loadAddress (   
   ULONGLONG NewVal  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `NewVal`  
 'ndaki Yürütülebilir dosya için yükleme adresi.  
  
## <a name="remarks"></a>Açıklamalar  
 Sembol sanal adresi (VA) özellikleri bu yöntemin değeri kullanılarak hesaplanır. Bu özellik sıfır dışında bir değer olarak ayarlanmadığı takdirde sanal adresler hesaplanmaz.  
  
> [!NOTE]
> Bu yöntemi, [IDiaSession](../../debugger/debug-interface-access/idiasession.md) nesnesini alırken ve semboller üzerinde herhangi bir sanal özelliği kullanmanız gerekiyorsa nesneyi kullanmaya başlamadan önce çağırmanız gerekir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)

---
title: 'IDiaSymbol:: get_acceleratorPointerTags | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
ms.assetid: 30e13cee-e511-49ec-affd-99b0097071b2
caps.latest.revision: 6
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 829c7a0193ce2742959f677e95dd4a499997cf5b
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149837"
---
# <a name="idiasymbolget_acceleratorpointertags"></a>IDiaSymbol::get_acceleratorPointerTags
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

C++ AMP Hızlandırıcı saplama işlevine karşılık gelen tüm Hızlandırıcı işaretçisi etiketi değerlerini döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT get_acceleratorPointerTags(   
   DWORD          cnt,  
   DWORD*         pcnt,  
   DWORD*         pPointerTags);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cnt`  
 'ndaki Çıktı dizisinin boyutu `pPointerTags` .  
  
 `pcnt`  
 dışı C++ AMP Hızlandırıcı saplama işlevindeki Hızlandırıcı işaretçisi etiketlerinin sayısı.  
  
 `pPointerTags`  
 dışı `DWORD` C++ amp Hızlandırıcı saplama işlevindeki Hızlandırıcı işaretçisi etiket değerleriyle doldurulmuş bir dizi işaretçisi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, `IDiaSymbol` C++ amp Hızlandırıcı saplama işlevine karşılık gelen bir arabirim üzerinde çağrılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)

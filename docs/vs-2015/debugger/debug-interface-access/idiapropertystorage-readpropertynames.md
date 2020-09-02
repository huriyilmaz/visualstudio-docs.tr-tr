---
title: 'IDiaPropertyStorage:: ReadPropertyNames | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-debug
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- IDiaPropertyStorage::ReadPropertyNames
ms.assetid: f8bcab77-afca-4a8f-8710-697842f8a518
caps.latest.revision: 13
author: MikeJo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: f3f6d3ac520a396b5207767a3fec0913c801c287
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62537426"
---
# <a name="idiapropertystoragereadpropertynames"></a>IDiaPropertyStorage::ReadPropertyNames
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Verilen özellik tanımlayıcıları için karşılık gelen dize adlarını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT ReadPropertyNames (  
   ULONG         cpropid,  
   PROPID const* rgpropid,  
   BSTR*         rglpwstrName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `cpropid`  
 'ndaki İçindeki özellik kimliği sayısı `rgpropid` .  
  
 `rgpropid`  
 'ndaki Adların alınacağı özellik kimliklerinin dizisi ( `PROPID` WTypes. h olarak bir olarak tanımlanır `ULONG` ).  
  
 `rglpwstrName`  
 [in, out] Belirtilen özellik kimlikleri için özellik adları dizisi. Dizi, istenen özellik adı sayısını tutmak için önceden ayrılmış olmalıdır ve en az dizeleri tutabilecek olmalıdır `cpropid``BSTR` .  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Döndürülen özellik adları artık gerekli olmadığında serbest bırakılmalıdır (işlevi çağırarak `SysFreeString` ).  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDiaPropertyStorage](../../debugger/debug-interface-access/idiapropertystorage.md)

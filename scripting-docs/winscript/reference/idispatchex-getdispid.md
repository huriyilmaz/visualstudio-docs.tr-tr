---
title: 'IDispatchEx:: Getdıspıd | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetDispID
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetDispID method
ms.assetid: a288d63d-b08a-4540-9d9d-0bcd182eff9a
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 81bb33a1e793f38e15dc51b37c4fa062eb54e7fa
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144539"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Tek bir üye adını karşılık gelen bir DISPID ile eşleştirir, daha sonra öğesine sonraki çağrılarında kullanılabilir `IDispatchEx::InvokeEx` .  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetDispID(  
   BSTR bstrName,  
   DWORD grfdex,  
   DISPID *pid  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bstrName`  
 Eşlenen ad geçirildi.  
  
 `grfdex`  
 Üye tanımlayıcısını alma seçeneklerini belirler. Bu, aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Değer|Anlamı|  
|-----------|-------------|  
|fdexNameCaseSensitive|Ad aramasının, büyük/küçük harfe duyarlı bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarlı aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
|Fdexnamegarantilemek|Zaten mevcut değilse, üyenin oluşturulmasını ister. Yeni üyenin değeriyle oluşturulması gerekir `VT_EMPTY` .|  
|Fdexnameörtük|Temel nesne açıkça belirtilmediği zaman çağıranın belirli bir ada üye için nesne (ler) aradığını gösterir.|  
|Fdexnamecaseduyarsız|Ad aramasının, büyük/küçük harfe duyarsız bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarsız aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
  
 `pid`  
 DISPID sonucu almak için çağıran tarafından ayrılan konuma yönelik işaretçi. Bir hata oluşursa, `pid` DISPID_UNKNOWN içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Anlamı|
|-|-|  
|`S_OK`|Başarılı.|  
|`E_OUTOFMEMORY`|Bellek yetersiz.|  
|`DISP_E_UNKNOWNNAME`|Ad bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetDispID`, `GetIDsOfNames` belirli bir üyeye AIT DISPID 'yi almak için yerine kullanılabilir.  
  
 `IDispatchEx`Üyelerin eklenmesi ve silinmesine izin verdiğinden, dispIDs kümesi bir nesnenin ömrü boyunca sabit kalmaz.  
  
 `riid`' De kullanılmayan parametre `IDispatch::GetIDsOfNames` kaldırıldı.  
  
## <a name="example"></a>Örnek  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
  
   // Assign to pdex and bstrName  
   pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid);  
   // Use dispid  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispatchEx Arabirimi](../../winscript/reference/idispatchex-interface.md)
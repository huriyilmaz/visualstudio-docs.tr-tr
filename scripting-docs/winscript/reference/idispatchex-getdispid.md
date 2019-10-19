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
ms.openlocfilehash: 57f0faf6004e2219600f0dbd63749a7e65ca438c
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576599"
---
# <a name="idispatchexgetdispid"></a>IDispatchEx::GetDispID
Tek bir üye adını karşılık gelen bir DISPID ile eşleştirir, bu daha sonra `IDispatchEx::InvokeEx` sonraki çağrılarında kullanılabilir.  
  
## <a name="syntax"></a>Sözdizimi  
  
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
  
|Değer|Açıklama|  
|-----------|-------------|  
|fdexNameCaseSensitive|Ad aramasının, büyük/küçük harfe duyarlı bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarlı aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
|Fdexnamegarantilemek|Zaten mevcut değilse, üyenin oluşturulmasını ister. Yeni üyenin `VT_EMPTY` değer ile oluşturulması gerekir.|  
|Fdexnameörtük|Temel nesne açıkça belirtilmediği zaman çağıranın belirli bir ada üye için nesne (ler) aradığını gösterir.|  
|Fdexnamecaseduyarsız|Ad aramasının, büyük/küçük harfe duyarsız bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarsız aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
  
 `pid`  
 DISPID sonucu almak için çağıran tarafından ayrılan konuma yönelik işaretçi. Bir hata oluşursa, `pid` DISPID_UNKNOWN içerir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|`E_OUTOFMEMORY`|Bellek yetersiz.|  
|`DISP_E_UNKNOWNNAME`|Ad bilinmiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 `GetDispID`, belirli bir üyenin DISPID 'sini almak için `GetIDsOfNames` yerine kullanılabilir.  
  
 @No__t_0 üyelerin eklenmesi ve silinmesine izin verdiğinden, dispIDs kümesi bir nesnenin ömrü boyunca sabit kalmaz.  
  
 @No__t_1 kullanılmayan `riid` parametresi kaldırıldı.  
  
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
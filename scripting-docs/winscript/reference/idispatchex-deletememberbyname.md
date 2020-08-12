---
title: IDispatchEx::D eleteMemberByName | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.DeleteMemberByName
apilocation:
- scrobj.dll
helpviewer_keywords:
- DeleteMemberByName method
ms.assetid: a01b4e6a-d989-4b29-bb3f-04554f8c39f7
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: cf62972b192d73bd130d15066d79ea70fe24beb8
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144603"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Üyeyi ada göre siler.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bstrName`  
 Silinecek üyenin adı.  
  
 `grfdex`  
 Üye adının büyük/küçük harfe duyarlı olup olmadığını belirler. Bu değer aşağıdakilerden biri olabilir:  
  
|Değer|Anlamı|  
|-----------|-------------|  
|fdexNameCaseSensitive|Ad aramasının, büyük/küçük harfe duyarlı bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarlı aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
|Fdexnamecaseduyarsız|Ad aramasının, büyük/küçük harfe duyarsız bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarsız aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Anlamı|
|-|-|  
|`S_OK`|Başarılı.|  
|`S_FALSE`|Üye var, ancak silinemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye silinirse, DISPID 'nin için geçerli kalması gerekir `GetNextDispID` .  
  
 Verilen ada sahip bir üye silinirse ve daha sonra aynı ada sahip bir üye yeniden oluşturulduğunda, DISPID aynı olmalıdır. (Yalnızca büyük/küçük harfe göre farklılık gösteren Üyeler nesneye bağımlıdır.)  
  
## <a name="example"></a>Örnek  
  
```cpp
BSTR bstrName;  
IDispatchEx *pdex;  
  
// Assign to pdex and bstrName  
pdex->DeleteMemberByName(bstrName, fdexNameCaseSensitive);  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispatchEx Arabirimi](../../winscript/reference/idispatchex-interface.md)
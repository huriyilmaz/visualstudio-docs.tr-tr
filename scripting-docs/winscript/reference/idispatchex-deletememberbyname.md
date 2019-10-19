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
ms.openlocfilehash: 2abb562f65885ee1d12f2ec9b2300fcddd3be37b
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72576620"
---
# <a name="idispatchexdeletememberbyname"></a>IDispatchEx::DeleteMemberByName
Üyeyi ada göre siler.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT DeleteMemberByName(  
   BSTR bstrName,  
   DWORD grfdex  
  
```  
  
#### <a name="parameters"></a>Parametreler  
 `bstrName`  
 Silinecek üyenin adı.  
  
 `grfdex`  
 Üye adının büyük/küçük harfe duyarlı olup olmadığını belirler. Bu, aşağıdaki değerlerden biri olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|fdexNameCaseSensitive|Ad aramasının, büyük/küçük harfe duyarlı bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarlı aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
|Fdexnamecaseduyarsız|Ad aramasının, büyük/küçük harfe duyarsız bir şekilde yapılmasını ister. , Büyük/küçük harfe duyarsız aramayı desteklemeyen nesne tarafından yoksayılabilir.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
|-|-|  
|`S_OK`|Başarılı.|  
|`S_FALSE`|Üye var, ancak silinemez.|  
  
## <a name="remarks"></a>Açıklamalar  
 Üye silinirse, DISPID 'nin `GetNextDispID` için geçerli kalması gerekir.  
  
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
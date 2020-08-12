---
title: 'IDispatchEx:: GetMemberProperties | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberProperties
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberProperties method
ms.assetid: 20d43209-12e2-472a-9bf3-81eced137b71
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 488f8790ec25532fb611f18e8b24e7e7dba2e2f4
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144561"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Üyenin özelliklerini alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 Üyeyi tanımlar. `GetDispID` `GetNextDispID` Dağıtım tanımlayıcısını almak için veya kullanır.  
  
 `grfdexFetch`  
 Alınacak özellikleri belirler. Bu, `pgrfdex` ve/veya aşağıdaki değerlerin bir birleşimi altında listelenen değerlerin bir birleşimi olabilir:  
  
|Değer|Anlamı|  
|-----------|-------------|  
|grfdexPropCanAll|FdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, Fdexpropcanyapýve fdexPropCanSourceEvents ' i birleştirir.|  
|grfdexPropCannotAll|FdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, Fdexpropcannotyapýsý ve fdexPropCannotSourceEvents ' i birleştirir.|  
|grfdexPropExtraAll|FdexPropNoSideEffects ve fdexPropDynamicType 'yi birleştirir.|  
|grfdexPropAll|GrfdexPropCanAll, grfdexPropCannotAll ve grfdexPropExtraAll birleştirir.|  
  
 `pgrfdex`  
 `DWORD`İstenen özellikleri alan a 'nın adresi. Bu, aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Değer|Anlamı|  
|-----------|-------------|  
|fdexPropCanGet|Üye DISPATCH_PROPERTYGET kullanılarak elde edilebilir.|  
|fdexPropCannotGet|Üye DISPATCH_PROPERTYGET kullanılarak elde edilemez.|  
|fdexPropCanPut|Üye DISPATCH_PROPERTYPUT kullanılarak ayarlanabilir.|  
|fdexPropCannotPut|Üye DISPATCH_PROPERTYPUT kullanılarak ayarlanamaz.|  
|fdexPropCanPutRef|Üye DISPATCH_PROPERTYPUTREF kullanılarak ayarlanabilir.|  
|fdexPropCannotPutRef|Üye DISPATCH_PROPERTYPUTREF kullanılarak ayarlanamaz.|  
|fdexPropNoSideEffects|Üyenin yan etkileri yok. Örneğin, hata ayıklayıcı hata ayıklamakta olan betiğin durumunu değiştirmeden bu üyeyi güvenle alabilir/ayarlayabilir/çağırabilir.|  
|fdexPropDynamicType|Üye dinamiktir ve nesnenin ömrü boyunca değişebilir.|  
|fdexPropCanCall|Üye, DISPATCH_METHOD kullanarak bir yöntem olarak çağrılabilir.|  
|fdexPropCannotCall|Üye, DISPATCH_METHOD kullanan bir yöntem olarak çağrılamaz.|  
|Fdexpropcanyapı|Üye, DISPATCH_CONSTRUCT kullanarak bir Oluşturucu olarak çağrılabilir.|  
|Fdexpropcannotyapýsý|Üye, DISPATCH_CONSTRUCT kullanan bir Oluşturucu olarak çağrılamaz.|  
|fdexPropCanSourceEvents|Üye etkinlikleri tetikedebilir.|  
|fdexPropCannotSourceEvents|Üye olayları tetiklemez.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Anlamı|
|-|-|  
|`S_OK`|Başarılı.|  
|`DISP_E_UNKNOWNNAME`|Ad bilinmiyor.|  
  
## <a name="example"></a>Örnek  
  
```cpp
BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;   
   DWORD dwProps;  
  
   // Assign to pdex and bstrName  
   if (SUCCEEDED(pdex->GetDispID(bstrName, fdexNameCaseSensitive, &dispid)) &&  
      SUCCEEDED(pdex->GetMemberProperties(dispid, grfdexPropAll, &dwProps)) &&  
         (dwProps & fdexPropCanPut))  
   {  
      // Assign to member  
   }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispatchEx arabirimi](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: Getdıspıd](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)
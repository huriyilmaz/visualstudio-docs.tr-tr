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
ms.openlocfilehash: 8016eef7b6e0da9b9fc88695db845cba7f608ff3
ms.sourcegitcommit: 184e2ff0ff514fb980724fa4b51e0cda753d4c6e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/18/2019
ms.locfileid: "72574094"
---
# <a name="idispatchexgetmemberproperties"></a>IDispatchEx::GetMemberProperties
Üyenin özelliklerini alır.  
  
## <a name="syntax"></a>Sözdizimi  
  
```cpp
HRESULT GetMemberProperties(  
   DISPID id,  
   DWORD grfdexFetch,  
   DWORD *pgrfdex  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 Üyeyi tanımlar. Dağıtım tanımlayıcısını almak için `GetDispID` veya `GetNextDispID` kullanır.  
  
 `grfdexFetch`  
 Alınacak özellikleri belirler. Bu, `pgrfdex` ve/veya aşağıdaki değerlerin bir birleşimi olarak listelenen değerlerin bir birleşimi olabilir:  
  
|Değer|Açıklama|  
|-----------|-------------|  
|grfdexPropCanAll|FdexPropCanGet, fdexPropCanPut, fdexPropCanPutRef, fdexPropCanCall, Fdexpropcanyapýve fdexPropCanSourceEvents ' i birleştirir.|  
|grfdexPropCannotAll|FdexPropCannotGet, fdexPropCannotPut, fdexPropCannotPutRef, fdexPropCannotCall, Fdexpropcannotyapýsý ve fdexPropCannotSourceEvents ' i birleştirir.|  
|grfdexPropExtraAll|FdexPropNoSideEffects ve fdexPropDynamicType 'yi birleştirir.|  
|grfdexPropAll|GrfdexPropCanAll, grfdexPropCannotAll ve grfdexPropExtraAll birleştirir.|  
  
 `pgrfdex`  
 İstenen özellikleri alan `DWORD` adresi. Bu, aşağıdaki değerlerin bir birleşimi olabilir:  
  
|Değer|Açıklama|  
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
|fdexPropCannotCall|Üye, DISPATCH_METHOD kullanarak bir yöntem olarak çağrılamaz.|  
|Fdexpropcanyapı|Üye, DISPATCH_CONSTRUCT kullanarak bir Oluşturucu olarak çağrılabilir.|  
|Fdexpropcannotyapýsý|Üye, DISPATCH_CONSTRUCT kullanan bir Oluşturucu olarak çağrılamaz.|  
|fdexPropCanSourceEvents|Üye etkinlikleri tetikedebilir.|  
|fdexPropCannotSourceEvents|Üye olayları tetiklemez.|  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|||  
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
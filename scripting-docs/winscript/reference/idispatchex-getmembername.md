---
title: 'IDispatchEx:: GetMemberName | Microsoft Docs'
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- IDispatchEx.GetMemberName
apilocation:
- scrobj.dll
helpviewer_keywords:
- GetMemberName method
ms.assetid: 5e59b63c-b781-4b90-88fd-40603a379a2d
caps.latest.revision: 8
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 8dbfb82e986ed6d1738bcc0cffeec35e5ba4515c
ms.sourcegitcommit: d281d2a04a5bc302650eebf369946d8f101e59dd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2020
ms.locfileid: "88144616"
---
# <a name="idispatchexgetmembername"></a>IDispatchEx::GetMemberName
Üyenin adını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp
HRESULT GetMemberName(  
   DISPID id,  
   BSTR *pbstrName  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `id`  
 Üyeyi tanımlar. `GetDispID` `GetNextDispID` Dağıtım tanımlayıcısını almak için veya kullanır.  
  
 `pbstrName`  
 `BSTR`Üyenin adını alan bir adresi. Çağıran uygulama, bu değeri boşaltmaktan sorumludur.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Aşağıdaki değerlerden birini döndürür:  
  
|Değer|Anlamı|
|-|-|  
|`S_OK`|Başarılı.|  
|`DISP_E_UNKNOWNNAME`|Ad bilinmiyor.|  
  
## <a name="example"></a>Örnek  
  
```cpp
HRESULT hr;  
   BSTR bstrName;  
   DISPID dispid;  
   IDispatchEx *pdex;  
  
   // Assign to pdex  
   hr = pdex->GetNextDispID(fdexEnumAll, DISPID_STARTENUM, &dispid);  
   while (hr == NOERROR)  
   {  
      hr = pdex->GetMemberName(dispid, &bstrName);  
      if (!wcscmp(bstrName, OLESTR("Bar")))  
      {  
         SysFreeString(bstrName);  
         return TRUE;  
      }  
   SysFreeString(bstrName);  
   hr = pdex->GetNextDispID(fdexEnumAll, dispid, &dispid);  
   }  
```  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [IDispatchEx arabirimi](../../winscript/reference/idispatchex-interface.md)   
 [IDispatchEx:: Getdıspıd](../../winscript/reference/idispatchex-getdispid.md)   
 [IDispatchEx::GetNextDispID](../../winscript/reference/idispatchex-getnextdispid.md)
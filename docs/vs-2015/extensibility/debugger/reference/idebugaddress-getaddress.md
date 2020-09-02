---
title: 'IDebugAddress:: GetAddress | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugAddress::GetAddress
helpviewer_keywords:
- IDebugAddress:GetAddress method
ms.assetid: 2590387b-5d36-4116-9a75-737957b8898e
caps.latest.revision: 7
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: f4d3263ca020f491e0c1cf20ee49792cacfbc362
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68186683"
---
# <a name="idebugaddressgetaddress"></a>IDebugAddress::GetAddress
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bir nesneyi ve onun kapsam veya kapsayıcısı içindeki konumunu açıklayan bir yapı döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp  
HRESULT GetAddress (  
   DEBUG_ADDRESS * pAddress  
);  
```  
  
```csharp  
int GetAddress(  
   DEBUG_ADDRESS[] pAddress  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pAddress`  
 [in, out] Bu yöntem tarafından doldurulan bir [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısı.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa S_OK döndürür; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) yapısı bu yönteme geçirilir ve ardından bunu ilgili bilgilerle doldurur. Bu bilgilerin nasıl yorumlanacağı, döndürülen bilgi türüne ve sembol işleyicisine bağlıdır. Daha fazla bilgi için bkz. [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [DEBUG_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)

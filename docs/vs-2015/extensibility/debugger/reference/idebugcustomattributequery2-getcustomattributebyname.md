---
title: 'IDebugCustomAttributeQuery2:: GetCustomAttributeByName | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
helpviewer_keywords:
- IDebugCustomAttributeQuery2::GetCustomAttributeByName
ms.assetid: 7428dfeb-8929-41b2-9b99-cb343a86c02d
caps.latest.revision: 10
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e1af059cf4319c18b8f8bb63e7b50ec3d2822e93
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62568440"
---
# <a name="idebugcustomattributequery2getcustomattributebyname"></a>IDebugCustomAttributeQuery2::GetCustomAttributeByName
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Özel özniteliğin adı verilen özel öznitelik baytlarını edinir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetCustomAttributeByName(   
   LPCOLESTR pszCustomAttributeName,  
   BYTE*     ppBlob,  
   DWORD*    pdwLen  
);  
```  
  
```csharp  
int GetCustomAttributeByName(  
   [In] string        pszCustomAttributeName,   
   [In, Out] byte[]   ppBlob,   
   [In, Out] ref uint pdwLen  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszCustomAttributeName`  
 'ndaki Aranacak özel özniteliğin adını içeren bir dize.  
  
 `ppBlob`  
 [in, out] Özel öznitelik baytları ile doldurulmuş bir dizi.  
  
 `pdwLen`  
 [in, out] Dizide döndürülecek en fazla bayt sayısını belirtir `ppBlob` ve gerçekten diziye yazılan bayt sayısını döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, özel öznitelik yoksa S_OK döndürür veya S_FALSE döndürür. Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `ppBlob`Kullanılabilir öznitelik baytları sayısını döndürmek için parametreyi null değere ayarlayın. Sonra bir dizi ayırın ve bu diziyi parametresi için geçirin `ppBlob` .  
  
 Öznitelik baytları özel özniteliğin ham verilerini temsil eder.  
  
 `ppBlob`Ve `pdwLen` parametreleri null bir değere ayarlanırsa, bu yöntem özel özniteliğin yalnızca mevcut olup olmadığını anlamak için kullanılabilir. Ancak, daha kolay bir alternatif, [ıcustomattributedefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md) yöntemini çağırmaktır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCustomAttributeQuery2](../../../extensibility/debugger/reference/idebugcustomattributequery2.md)   
 [IsCustomAttributeDefined](../../../extensibility/debugger/reference/idebugcustomattributequery2-iscustomattributedefined.md)

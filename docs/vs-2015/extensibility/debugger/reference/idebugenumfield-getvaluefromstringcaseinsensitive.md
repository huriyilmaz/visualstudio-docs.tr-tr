---
title: 'Ihata ayıklama Genumfield:: Getvaluefromstringcaseduyarsız | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive
helpviewer_keywords:
- IDebugEnumField::GetValueFromStringCaseInsensitive method
ms.assetid: ef95b38e-d9b2-4fb5-a166-7c2e14641dc7
caps.latest.revision: 9
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: efe94a721c432cb1284df299ca267271ab5bef4d
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188925"
---
# <a name="idebugenumfieldgetvaluefromstringcaseinsensitive"></a>IDebugEnumField::GetValueFromStringCaseInsensitive
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bir numaralandırma sabiti adı ile ilişkili değeri döndürmek için büyük/küçük harf duyarsız bir arama kullanır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetValueFromStringCaseInsensitive(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```csharp  
int GetValueFromStringCaseInsensitive(  
   string    pszValue,   
   out ulong pValue  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszValue`  
 'ndaki Değerin alınacağı adı belirten bir dize. C++ için bu, geniş bir karakter dizesidir.  
  
 `pValue`  
 dışı İlişkili sayısal değeri döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, `S_FALSE` ad numaralandırmanın bir parçası değilse, veya bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntem, büyük/küçük harfe duyarlıdır. Büyük/küçük harfe duyarlı bir arama gerekiyorsa (örneğin, adların büyük/küçük harfe duyarlı olduğu C++ gibi bir dilde) [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)kullanın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ihata ayıklama Genumalanı](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromString](../../../extensibility/debugger/reference/idebugenumfield-getvaluefromstring.md)

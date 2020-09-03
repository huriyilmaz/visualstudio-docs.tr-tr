---
title: 'Ihata ayıklama Gpoınterfield:: Getbaşvurunun Encedfield | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugPointerField::GetDereferencedField
helpviewer_keywords:
- IDebugPointerField::GetDereferencedField method
ms.assetid: 8de988ab-cd79-4287-be72-3c900f2fe407
caps.latest.revision: 8
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 02197f660189d4caf374fc5927f349fd5fc6b8b5
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68201018"
---
# <a name="idebugpointerfieldgetdereferencedfield"></a>IDebugPointerField::GetDereferencedField
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, bu işaretçi nesnesinin işaret ettiği nesne türünü döndürür.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetDereferencedField(  
   IDebugField** ppField  
);  
```  
  
```csharp  
int GetDereferencedField(  
   out IDebugField ppField  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `ppField`  
 dışı Hedef nesnenin türünü açıklayan bir [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Örneğin, [ıdebuggpoınterfield](../../../extensibility/debugger/reference/idebugpointerfield.md) nesnesi bir tamsayıya işaret ediyorsa, bu yöntem tarafından döndürülen [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) türü bu tamsayı türünü açıklar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Ihata ayıklama Gpoınterfield](../../../extensibility/debugger/reference/idebugpointerfield.md)   
 [IDebugField](../../../extensibility/debugger/reference/idebugfield.md)

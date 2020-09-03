---
title: 'IDebugDocumentContext2:: GetSourceRange | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugDocumentContext2::GetSourceRange
helpviewer_keywords:
- IDebugDocumentContext2::GetSourceRange
ms.assetid: 5903c75e-5390-4d13-9314-1ee276255313
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bcec6af2b8e7b1acfdc9c3cf38cb18654be78c53
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68145008"
---
# <a name="idebugdocumentcontext2getsourcerange"></a>IDebugDocumentContext2::GetSourceRange
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu belge bağlamının kaynak kodu aralığını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetSourceRange(   
   TEXT_POSITION* pBegPosition,  
   TEXT_POSITION* pEndPosition  
);  
```  
  
```csharp  
int GetSourceRange(   
   TEXT_POSITION[] pBegPosition,  
   TEXT_POSITION[] pEndPosition  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBegPosition`  
 [in, out] Başlangıç konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.  
  
 `pEndPosition`  
 [in, out] Bitiş konumuyla doldurulmuş bir [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) yapısı. Bu bilgi gerekmiyorsa bu bağımsız değişkeni null bir değer olarak ayarlayın.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Kaynak aralığı, geçerli deyimden hemen hemen sonra koda katkıda bulunan önceki deyimden hemen sonra olmak üzere, kaynak kodu aralığıdır. Kaynak aralığı genellikle, açıklamalar dahil olmak üzere kaynak deyimlerini, ayrıştırma penceresindeki kodla birlikte karıştırmak için kullanılır.  
  
 Yalnızca bu belge bağlamı içinde yer alan kod deyimlerinin aralığını almak için [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md) yöntemini çağırın.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)   
 [GetStatementRange](../../../extensibility/debugger/reference/idebugdocumentcontext2-getstatementrange.md)   
 [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

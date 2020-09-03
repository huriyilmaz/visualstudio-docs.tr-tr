---
title: 'IDebugThread2:: Setnextdeyimizi | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugThread2::SetNextStatement
helpviewer_keywords:
- IDebugThread2::SetNextStatement
ms.assetid: 9e2834dd-4ecf-45af-8e6c-f9318ebdac06
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 755044ec1d713075c1c1fd3165254ba192943288
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68152968"
---
# <a name="idebugthread2setnextstatement"></a>IDebugThread2::SetNextStatement
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Geçerli yönerge işaretçisini verilen kod bağlamına ayarlar.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT SetNextStatement (   
   IDebugStackFrame2*  pStackFrame,  
   IDebugCodeContext2* pCodeContext  
);  
```  
  
```csharp  
int SetNextStatement (   
   IDebugStackFrame2  pStackFrame,  
   IDebugCodeContext2 pCodeContext  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pStackFrame`  
 Gelecekte kullanılmak üzere ayrılmıştır; null değere ayarlayın.  
  
 `pCodeContext`  
 'ndaki Yürütülmesi ve bağlamı için kod konumunu açıklayan bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda olası diğer değerler gösterilmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_NONLEAF_FRAME|Sonraki ifade, çerçeve yığınında daha derin bir yığın çerçevesinde olamaz.|  
|E_CANNOT_SETIP_TO_DIFFERENT_FUNCTION|Sonraki ifade, yığındaki herhangi bir kareyle ilişkili değildir.|  
|E_CANNOT_SET_NEXT_STATEMENT_ON_EXCEPTION|Bazı hata ayıklama motorları bir özel durumdan sonra sonraki ifadeyi ayarlayamıyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Yönerge işaretçisi, yürütülecek bir sonraki yönergeyi veya ifadeyi gösterir. Bu yöntem, kaynak kodu satırını yeniden denemek veya yürütmeye zorlamak için, örneğin başka bir işlevde devam etmek için kullanılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)   
 [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)

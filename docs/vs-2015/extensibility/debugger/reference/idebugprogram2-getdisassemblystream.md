---
title: 'IDebugProgram2:: GetDisassemblyStream | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProgram2::GetDisassemblyStream
helpviewer_keywords:
- IDebugProgram2::GetDisassemblyStream
ms.assetid: beda0da5-267e-4bf3-96c4-b659d29e2254
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 6f918b9895975554534ef1702334d7a006112f77
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68202725"
---
# <a name="idebugprogram2getdisassemblystream"></a>IDebugProgram2::GetDisassemblyStream
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu program veya bu programın bir parçası için ayrıştırma akışını alır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT GetDisassemblyStream(   
   DISASSEMBLY_STREAM_SCOPE   dwScope,  
   IDebugCodeContext2*        pCodeContext,  
   IDebugDisassemblyStream2** ppDisassemblyStream  
);  
```  
  
```csharp  
int GetDisassemblyStream(   
   enum_DISASSEMBLY_STREAM_SCOPE  dwScope,  
   IDebugCodeContext2             pCodeContext,  
   out IDebugDisassemblyStream2   ppDisassemblyStream  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `dwScope`  
 'ndaki Ayrıştırılmış akışın kapsamını tanımlayan [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) numaralandırmasından bir değer belirtir.  
  
 `pCodeContext`  
 'ndaki Ayrıştırılmış birleştirme akışının başlayacağı konumu temsil eden bir [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) nesnesi.  
  
 `ppDisassemblyStream`  
 dışı Ayrıştırılmış derlemeyi temsil eden bir [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. `E_DISASM_NOTSUPPORTED`Bu belirli mimari için ayrıştırılmış derleme desteklenmiyorsa döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 `dwScopes`Parametre `DSS_HUGE` [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md) numaralandırma kümesi bayrağıyla ayarlandıysa, ayrıştırılmış bir dosyanın veya modülün tamamı için, örneğin, çok sayıda ayrıştırma yönergesi döndürmesi beklenir. `DSS_HUGE`Bayrak ayarlanmamışsa, ayrıştırılmış derlemenin küçük bir bölgeye göre sınırlandırılan genellikle tek bir işlevde olması beklenir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)   
 [DISASSEMBLY_STREAM_SCOPE](../../../extensibility/debugger/reference/disassembly-stream-scope.md)   
 [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)   
 [IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)

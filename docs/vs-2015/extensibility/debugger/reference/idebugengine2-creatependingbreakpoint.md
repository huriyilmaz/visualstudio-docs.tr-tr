---
title: 'IDebugEngine2:: CreatePendingBreakpoint | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngine2::CreatePendingBreakpoint
helpviewer_keywords:
- IDebugEngine2::CreatePendingBreakpoint
ms.assetid: 92e85b90-a931-48d9-89a7-a6edcb83ae5a
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 84c36d08c7ad907006eb9f41d2f6e2c9cd77e7bf
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68196039"
---
# <a name="idebugengine2creatependingbreakpoint"></a>IDebugEngine2::CreatePendingBreakpoint
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Hata ayıklama altyapısında (DE) bekleyen bir kesme noktası oluşturur.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT CreatePendingBreakpoint(   
   IDebugBreakpointRequest2*  pBPRequest,  
   IDebugPendingBreakpoint2** ppPendingBP  
);  
```  
  
```csharp  
int CreatePendingBreakpoint(   
   IDebugBreakpointRequest2     pBPRequest,  
   out IDebugPendingBreakpoint2 ppPendingBP  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pBPRequest`  
 'ndaki Oluşturulacak bekleyen kesme noktasını açıklayan bir [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md) nesnesi.  
  
 `ppPendingBP`  
 dışı Bekleyen kesme noktasını temsil eden bir [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesi döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Genellikle parametresi `E_FAIL` `pBPRequest` , `pBPRequest` parametresi geçersiz veya eksik ise öğesinin tarafından desteklenen herhangi bir dille eşleşmezse döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bekleyen bir kesme noktası aslında koda bir kesme noktası bağlamak için gereken tüm bilgilerin bir koleksiyonudur. Bu yöntemden döndürülen bekleyen kesme noktası, [bağlama](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md) yöntemi çağrılana kadar koda bağlı değildir.  
  
 Kullanıcı kümelerinin bekleyen her bir kesme noktası için, oturum hata ayıklama Yöneticisi (SDM), her bir ekli de bu yöntemi çağırır. Kesme noktasının, bu de çalıştıran programlar için geçerli olduğunu doğrulamak için DE vardır.  
  
 Kullanıcı bir kod satırında bir kesme noktası ayarladığında, kesme noktasını bu koda karşılık gelen belgedeki en yakın çizgiye bağlamak için DE serbest bırakılır. Bu, kullanıcının çok satırlı bir deyimin ilk satırında bir kesme noktası ayarlaması, ancak bunu son satıra bağlama (tüm kodun hata ayıklama bilgilerinde bulunduğu yer) için mümkün hale getirir.  
  
## <a name="example"></a>Örnek  
 Aşağıdaki örnek, basit bir nesne için bu yöntemin nasıl uygulanacağını gösterir `CProgram` . Uygulamasının uygulamasının uygulanması, her bir `IDebugEngine2::CreatePendingBreakpoint` programda yönteminin bu uygulamasına tüm çağrıları iletebilir.  
  
```  
HRESULT CProgram::CreatePendingBreakpoint(IDebugBreakpointRequest2* pBPRequest, IDebugPendingBreakpoint2** ppPendingBP)     
{    
  
   // Create and initialize the CPendingBreakpoint object.  
   CComObject<CPendingBreakpoint> *pPending;    
   CComObject<CPendingBreakpoint>::CreateInstance(&pPending);    
   pPending->Initialize(pBPRequest, m_pInterp, m_pCallback, m_pEngine);    
   return pPending->QueryInterface(ppPendingBP);    
}    
```  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)   
 [Bağladığınızda](../../../extensibility/debugger/reference/idebugpendingbreakpoint2-bind.md)   
 [IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)   
 [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)

---
title: 'IDebugProcess2:: Attach | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess2::Attach
helpviewer_keywords:
- IDebugProcess2::Attach
ms.assetid: 40d78417-fde2-45c3-96c9-16e06bd9008d
caps.latest.revision: 11
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 4d4664f164675c445510d8976f33577684dbd1d2
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68188103"
---
# <a name="idebugprocess2attach"></a>IDebugProcess2::Attach
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Oturum hata ayıklama yöneticisini (SDM) işleme iliştirir.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT Attach(   
   IDebugEventCallback2* pCallback,  
   GUID*                 rgguidSpecificEngines,  
   DWORD                 celtSpecificEngines,  
   HRESULT*              rghrEngineAttach  
);  
```  
  
```csharp  
int Attach(   
   IDebugEventCallback2 pCallback,  
   Guid[]               rgguidSpecificEngines,  
   uint                 celtSpecificEngines,  
   int[]                rghrEngineAttach  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pCallback`  
 'ndaki Hata ayıklama olayı bildiriminde kullanılan bir [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.  
  
 `rgguidSpecificEngines`  
 'ndaki İşlemde çalışan programlarda hata ayıklaması yapmak için kullanılacak hata ayıklama altyapısının GUID dizisi. Bu parametre null bir değer olabilir. Ayrıntılar için bkz. açıklamalar.  
  
 `celtSpecificEngines`  
 'ndaki Dizideki hata ayıklama altyapısının sayısı `rgguidSpecificEngines` ve `rghrEngineAttach` dizinin boyutu.  
  
 `rghrEngineAttach`  
 [in, out] Hata ayıklama altyapılarının döndürdüğü bir HRESULT kodları dizisi. Bu dizinin boyutu `celtSpecificEngines` parametresinde belirtilir. Her kod genellikle ya da `S_OK` olur `S_ATTACH_DEFERRED` . İkincisi, aynı anda hiçbir program için DE bağlı olduğunu gösterir.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür. Aşağıdaki tabloda olası diğer değerler gösterilmektedir.  
  
|Değer|Açıklama|  
|-----------|-----------------|  
|`E_ATTACH_DEBUGGER_ALREADY_ATTACHED`|Belirtilen işlem hata ayıklayıcıya zaten eklenmiş.|  
|`E_ATTACH_DEBUGGEE_PROCESS_SECURITY_VIOLATION`|İliştirme yordamı sırasında bir güvenlik ihlali oluştu.|  
|`E_ATTACH_CANNOT_ATTACH_TO_DESKTOP`|Bir masaüstü işlemi hata ayıklayıcıya eklenemiyor.|  
  
## <a name="remarks"></a>Açıklamalar  
 Bir işleme iliştirme, SDM 'yi dizide belirtilen hata ayıklama altyapıları (DE) tarafından ayıklanabilecek bu işlemde çalışan tüm programlara iliştirir `rgguidSpecificEngines` . `rgguidSpecificEngines`Parametresini null bir değer olarak ayarlayın veya `GUID_NULL` işlemdeki tüm programlara eklemek için diziye dahil edin.  
  
 İşlemde oluşan tüm hata ayıklama olayları verilen [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesine gönderilir. `IDebugEventCallback2`SDM Bu yöntemi çağırdığında bu nesne sağlanır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)

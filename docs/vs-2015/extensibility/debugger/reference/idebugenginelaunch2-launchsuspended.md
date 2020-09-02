---
title: 'IDebugEngineLaunch2:: Launchaskıya alındı | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
caps.latest.revision: 18
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 08f59f9f099f4cec52760c8a8364feb8f5481ffa
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68195749"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem hata ayıklama altyapısı (DE) yoluyla bir işlem başlatır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
HRESULT LaunchSuspended (   
   LPCOLESTR             pszMachine,  
   IDebugPort2*          pPort,  
   LPCOLESTR             pszExe,  
   LPCOLESTR             pszArgs,  
   LPCOLESTR             pszDir,  
   BSTR                  bstrEnv,  
   LPCOLESTR             pszOptions,  
   LAUNCH_FLAGS          dwLaunchFlags,  
   DWORD                 hStdInput,  
   DWORD                 hStdOutput,  
   DWORD                 hStdError,  
   IDebugEventCallback2* pCallback,  
   IDebugProcess2**      ppDebugProcess  
);  
```  
  
```csharp  
int LaunchSuspended(  
   string               pszServer,   
   IDebugPort2          pPort,   
   string               pszExe,   
   string               pszArgs,   
   string               pszDir,   
   string               bstrEnv,   
   string               pszOptions,   
   enum_LAUNCH_FLAGS    dwLaunchFlags,   
   uint                 hStdInput,   
   uint                 hStdOutput,   
   uint                 hStdError,  
   IDebugEventCallback2 pCallback,   
   out IDebugProcess2   ppProcess  
);  
```  
  
#### <a name="parameters"></a>Parametreler  
 `pszMachine`  
 'ndaki İşlemin çalıştırılacağı makinenin adı. Yerel makineyi belirtmek için null değeri kullanın.  
  
 `pPort`  
 'ndaki Programın çalışacağı bağlantı noktasını temsil eden [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimi.  
  
 `pszExe`  
 'ndaki Başlatılacak yürütülebilir dosyanın adı.  
  
 `pszArgs`  
 'ndaki Yürütülebilir dosyaya geçirilecek bağımsız değişkenler. Bağımsız değişken yoksa, null bir değer olabilir.  
  
 `pszDir`  
 'ndaki Yürütülebilir dosya tarafından kullanılan çalışma dizininin adı. Çalışma dizini gerekmiyorsa null değeri olabilir.  
  
 `bstrEnv`  
 'ndaki NULL ile sonlandırılmış dizelerin ortam bloğu ve ardından ek bir NULL Sonlandırıcı.  
  
 `pszOptions`  
 'ndaki Yürütülebilir dosya seçenekleri.  
  
 `dwLaunchFlags`  
 'ndaki Bir oturumun [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) belirtir.  
  
 `hStdInput`  
 'ndaki Alternatif bir giriş akışına işleyin. Yeniden yönlendirme gerekmiyorsa 0 olabilir.  
  
 `hStdOutput`  
 'ndaki Alternatif bir çıkış akışına işleyin. Yeniden yönlendirme gerekmiyorsa 0 olabilir.  
  
 `hStdError`  
 'ndaki Alternatif bir hata çıktı akışına işleyin. Yeniden yönlendirme gerekmiyorsa 0 olabilir.  
  
 `pCallback`  
 'ndaki Hata ayıklayıcı olaylarını alan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.  
  
 `ppDebugProcess`  
 dışı Başlatılan işlemi temsil eden elde edilen [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesini döndürür.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Normalde, [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] [launchaskıya alınan](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) yöntemini kullanarak bir programı başlatır ve ardından hata ayıklayıcıyı askıya alınmış programa iliştirir. Ancak, hata ayıklama altyapısının bir programı başlatması gerekebilecek durumlar vardır (örneğin, hata ayıklama altyapısı bir yorumlayıcının parçasıysa ve hata Ayıklanan program yorumlanan bir diliyorsa), bu durumda [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] `IDebugEngineLaunch2::LaunchSuspended` yöntemini kullanır.  
  
 İşlem askıya alınma durumunda başarılı bir şekilde başlatıldıktan sonra işlemi başlatmak için [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) yöntemi çağırılır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)   
 [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)   
 [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)   
 [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [Launchaskıya alındı](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)   
 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

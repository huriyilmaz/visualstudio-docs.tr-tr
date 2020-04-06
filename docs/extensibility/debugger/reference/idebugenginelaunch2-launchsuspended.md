---
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: e802c17d0a93aabbe5c6c0a8573abc6a551944ae
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80730550"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Bu yöntem hata ayıklama motoru (DE) yoluyla bir işlem başlatıyor.

## <a name="syntax"></a>Sözdizimi

```cpp
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

## <a name="parameters"></a>Parametreler
`pszMachine`\
[içinde] İşlemi başlatacak makinenin adı. Yerel makineyi belirtmek için null değeri kullanın.

`pPort`\
[içinde] Programın çalışacağı bağlantı noktasını temsil eden [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimi.

`pszExe`\
[içinde] Başlatılacak yürütülebilir adı.

`pszArgs`\
[içinde] Yürütülebilir geçmek için argümanlar. Bağımsız değişken yoksa null bir değer olabilir.

`pszDir`\
[içinde] Çalıştırılabilen tarafından kullanılan çalışma dizininin adı. Çalışma dizini gerekli değilse, null bir değer olabilir.

`bstrEnv`\
[içinde] NULL sonlandırılan dizelerin ortam bloğu ve ardından ek bir NULL sonlandırıcı.

`pszOptions`\
[içinde] Çalıştırılabilir için seçenekler.

`dwLaunchFlags`\
[içinde] Oturum için [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) belirtir.

`hStdInput`\
[içinde] Alternatif bir giriş akışına işitin. Yeniden yönlendirme gerekli değilse 0 olabilir.

`hStdOutput`\
[içinde] Alternatif bir çıktı akışına işitin. Yeniden yönlendirme gerekli değilse 0 olabilir.

`hStdError`\
[içinde] Alternatif bir hata çıktısı akışına işitin. Yeniden yönlendirme gerekli değilse 0 olabilir.

`pCallback`\
[içinde] Hata ayıklama olayları alan [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`ppDebugProcess`\
[çıkış] Başlatılan işlemi temsil eden ortaya çıkan [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Normalde [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) yöntemini kullanarak bir program başlatır ve hata ayıklamayı askıya alınan programa bağlar. Ancak, hata ayıklama altyapısının bir program başlatması gerekebileceği durumlar vardır (örneğin, hata ayıklama altyapısı bir yorumlayıcının parçasıysa ve [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] hata `IDebugEngineLaunch2::LaunchSuspended` ayıklanan program yorumlanmış bir dilse), bu durumda yöntemi kullanır.

 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) yöntemi, işlem askıya alınmış durumda başarıyla başlatıldıktan sonra işlemi başlatmak için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

---
description: Bu yöntem, hata ayıklama altyapısı (DE) ile bir işlemi başlatıyor.
title: IDebugEngineLaunch2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugEngineLaunch2::LaunchSuspended
helpviewer_keywords:
- IDebugEngineLaunch2::LaunchSuspended
ms.assetid: 5dd2643e-c20a-470e-9024-2a423eb39856
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 27d4ae71dfa2c5a1c0f1d7806e1fa83c511a1bfd7131667880dce3dc5b3db54a
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121390092"
---
# <a name="idebugenginelaunch2launchsuspended"></a>IDebugEngineLaunch2::LaunchSuspended
Bu yöntem, hata ayıklama altyapısı (DE) ile bir işlemi başlatıyor.

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
[in] İşlem başlatan makinenin adı. Yerel makineyi belirtmek için null değer kullanın.

`pPort`\
[in] Programın içinde çalıştıracak bağlantı noktasını temsil eden [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) arabirimi.

`pszExe`\
[in] Başlatacak yürütülebilir dosyanın adı.

`pszArgs`\
[in] Yürütülebilir dosyaya geçiş için bağımsız değişkenler. Bağımsız değişken yoksa null değer olabilir.

`pszDir`\
[in] Yürütülebilir dosya tarafından kullanılan çalışma dizininin adı. Çalışma dizini gerekmiyorsa null değer olabilir.

`bstrEnv`\
[in] NULL ile sonlandırılan dizelerin ortam bloğu, ardından ek bir NULL sonlandırıcısı.

`pszOptions`\
[in] Yürütülebilir dosya seçenekleri.

`dwLaunchFlags`\
[in] Oturum [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md) için geçerli olan yapılandırmayı belirtir.

`hStdInput`\
[in] Alternatif bir giriş akışına işle. Yeniden yönlendirme gerekli yoksa 0 olabilir.

`hStdOutput`\
[in] Alternatif bir çıkış akışına işle. Yeniden yönlendirme gerekli yoksa 0 olabilir.

`hStdError`\
[in] Alternatif bir hata çıkış akışını işle. Yeniden yönlendirme gerekli yoksa 0 olabilir.

`pCallback`\
[in] Hata [ayıklayıcı olaylarını alan IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi.

`ppDebugProcess`\
[out] Başlatılan işlemi temsil [eden sonuçta elde edilen IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) nesnesini döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Normalde, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md) yöntemini kullanarak bir program başlatıyor ve ardından hata ayıklayıcıyı askıya alınan programa iliştirer. Ancak, hata ayıklama altyapısının bir programı başlatması gereken durumlar olabilir (örneğin, hata ayıklama altyapısı bir yorumlayıcının parçası ise ve hata ayıklama yapılan program yorumlandı bir dilse), bu durumda [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] yöntemi `IDebugEngineLaunch2::LaunchSuspended` kullanır.

 [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md) yöntemi, işlem askıya alındıktan sonra başarıyla başlatıldıktan sonra işlemi başlatmak için çağrılır.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)
- [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md)
- [LAUNCH_FLAGS](../../../extensibility/debugger/reference/launch-flags.md)
- [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)
- [LaunchSuspended](../../../extensibility/debugger/reference/idebugportex2-launchsuspended.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md)

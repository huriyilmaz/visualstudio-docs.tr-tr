---
title: IDebugPortEx2::LaunchSuspended | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28ff6065bbe83852b5acc3ffe253a0bdabcc67ec
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80725104"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Çalıştırılabilir bir dosya başlatıyor.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT LaunchSuspended( 
   LPCOLESTR        pszExe,
   LPCOLESTR        pszArgs,
   LPCOLESTR        pszDir,
   BSTR             bstrEnv,
   DWORD            hStdInput,
   DWORD            hStdOutput,
   DWORD            hStdError,
   IDebugProcess2** ppPortProcess
);
```

```csharp
int LaunchSuspended( 
   string             pszExe,
   string             pszArgs,
   string             pszDir,
   string             bstrEnv,
   uint               hStdInput,
   uint               hStdOutput,
   uint               hStdError,
   out IDebugProcess2 ppPortProcess
);
```

## <a name="parameters"></a>Parametreler
`pszExe`\
[içinde] Başlatılacak yürütülebilir adı. Bu tam bir yol veya `pszDir` parametre belirtilen çalışma dizini göreli olabilir.

`pszArgs`\
[içinde] Yürütülebilir geçmek için argümanlar. Bağımsız değişken yoksa null bir değer olabilir.

`pszDir`\
[içinde] Çalıştırılabilen tarafından kullanılan çalışma dizininin adı. Çalışma dizini gerekli değilse, null bir değer olabilir.

`bstrEnv`\
[içinde] Null-sonlandırılan dizeleri çevre bloğu, ek bir NULL sonlandırıcı izledi.

`hStdInput`\
[içinde] Alternatif bir giriş akışına işitin. Yeniden yönlendirme gerekli değilse 0 olabilir.

`hStdOutput`\
[içinde] Alternatif bir çıktı akışına işitin. Yeniden yönlendirme gerekli değilse 0 olabilir.

`hStdError`\
[içinde] Alternatif bir hata çıktısı akışına işitin. Yeniden yönlendirme gerekli değilse 0 olabilir.

`ppPortProcess`\
[çıkış] Başlatılan işlemi temsil eden bir [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, askıya alınması ve herhangi bir kod çalışmaması için işlemi başlatmalıdır. [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) yöntemi işlemi devam ettirmek için çağrılır.

 Bir program hata ayıklama motorundan da başlatılabilir. Ayrıntılar için [bkz.](../../../extensibility/debugger/launching-a-program.md)

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Program Başlatma](../../../extensibility/debugger/launching-a-program.md)

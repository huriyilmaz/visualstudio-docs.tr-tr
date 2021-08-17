---
description: Yürütülebilir bir dosya başlatıyor.
title: IDebugPortEx2::LaunchSuspended | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugPortEx2::LaunchSuspended
helpviewer_keywords:
- IDebugPortEx2::LaunchSuspended
ms.assetid: 34b2cf99-2e52-4757-8969-1d12ac517ec0
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 0c6db6cc7f67cc8cb4106215d33eb791c551a66b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122030288"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Yürütülebilir bir dosya başlatıyor.

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
[in] Başlatacak yürütülebilir dosyanın adı. Bu tam yol veya parametresinde belirtilen çalışma diziniyle göreli `pszDir` olabilir.

`pszArgs`\
[in] Yürütülebilir dosyaya geçiş için bağımsız değişkenler. Bağımsız değişken yoksa null değer olabilir.

`pszDir`\
[in] Yürütülebilir dosya tarafından kullanılan çalışma dizininin adı. Çalışma dizini gerekmiyorsa null değer olabilir.

`bstrEnv`\
[in] Null sonlandırılan dizelerin ortam bloğu, ardından ek bir NULL sonlandırıcısı.

`hStdInput`\
[in] Alternatif bir giriş akışına işle. Yeniden yönlendirme gerekli yoksa 0 olabilir.

`hStdOutput`\
[in] Alternatif bir çıkış akışına işle. Yeniden yönlendirme gerekli yoksa 0 olabilir.

`hStdError`\
[in] Alternatif bir hata çıkış akışına işle. Yeniden yönlendirme gerekli yoksa 0 olabilir.

`ppPortProcess`\
[out] Başlatılan işlemi [temsil eden bir IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem işlemi başlatarak askıya alınarak herhangi bir kod çalıştırmama işleminin başlatılmasını sağlar. Işlemi [devam ettiren ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) yöntemi çağrılır.

 Bir program bir hata ayıklama altyapısından da başlatabilirsiniz. Ayrıntılar için [bkz. Program Başlatma.](../../../extensibility/debugger/launching-a-program.md)

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Program Başlatma](../../../extensibility/debugger/launching-a-program.md)

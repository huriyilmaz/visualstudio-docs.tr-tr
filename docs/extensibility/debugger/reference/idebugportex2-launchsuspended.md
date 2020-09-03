---
title: 'IDebugPortEx2:: Launchaskıya alındı | Microsoft Docs'
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
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80725104"
---
# <a name="idebugportex2launchsuspended"></a>IDebugPortEx2::LaunchSuspended
Yürütülebilir bir dosya başlatır.

## <a name="syntax"></a>Söz dizimi

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
'ndaki Başlatılacak yürütülebilir dosyanın adı. Bu, tam yol veya parametrede belirtilen çalışma dizinine göre olabilir `pszDir` .

`pszArgs`\
'ndaki Yürütülebilir dosyaya geçirilecek bağımsız değişkenler. Bağımsız değişken yoksa, null bir değer olabilir.

`pszDir`\
'ndaki Yürütülebilir dosya tarafından kullanılan çalışma dizininin adı. Çalışma dizini gerekmiyorsa null değeri olabilir.

`bstrEnv`\
'ndaki Null ile sonlandırılmış dizelerin ortam bloğu ve ardından ek bir NULL Sonlandırıcı.

`hStdInput`\
'ndaki Alternatif bir giriş akışına işleyin. Yeniden yönlendirme gerekmiyorsa 0 olabilir.

`hStdOutput`\
'ndaki Alternatif bir çıkış akışına işleyin. Yeniden yönlendirme gerekmiyorsa 0 olabilir.

`hStdError`\
'ndaki Alternatif bir hata çıktı akışına işleyin. Yeniden yönlendirme gerekmiyorsa 0 olabilir.

`ppPortProcess`\
dışı Başlatılan işlemi temsil eden bir [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md) nesnesi döndürür.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde, bir hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntem, askıya alınmış ve herhangi bir kod çalıştırmayan için işlemi başlatacaktır. İşlemi sürdürecek [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md) yöntemi çağırılır.

 Ayrıca, bir program hata ayıklama altyapısından başlatılabilir. Ayrıntılar için bkz. [Program başlatma](../../../extensibility/debugger/launching-a-program.md).

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md)
- [IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)
- [ResumeProcess](../../../extensibility/debugger/reference/idebugportex2-resumeprocess.md)
- [Program Başlatma](../../../extensibility/debugger/launching-a-program.md)

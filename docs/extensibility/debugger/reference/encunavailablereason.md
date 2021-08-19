---
description: Düzenle ve Devam'ın kullanılabilir olmadığının nedenlerini temsil eder.
title: EncUnavailableReason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: d14b48d4cc3e32c48886222919b5e1f80f72fc69
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160223"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!` Düzenle ve **Devam'ın kullanılabilir olmadığının** nedenlerini temsil eder.

## <a name="syntax"></a>Syntax

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
```

## <a name="fields"></a>Alanlar
`ENCUN_NONE`\
Düzenle ve Devam'ın kullanılabilir olmadığının belirli bir nedeni yoktur.

`ENCUN_INTEROP`\
Düzenle ve Devam' bir InterOp çağrısı sırasında kullanılamaz.

`ENCUN_SQLCLR`\
Düzenle ve Devam Edin, Ortak Dil Çalışma SQL (CLR) kullanan bir yordam çağrısı sırasında kullanılamaz.

`ENCUN_MINIDUMP`\
Mini döküm işleme sırasında Düzenle ve Devam Etmek kullanılamaz.

`ENCUN_EMBEDDED`\
Katıştırılmış kod işlenemezken Düzenle ve Devam Etmek kullanılamaz.

`ENCUN_ATTACH`\
Oturum hata ayıklayıcıya bağlı olduğundan, tarafından başlatılamay olduğundan Düzenle ve Devam Etmek kullanılamıyor.

`ENCUN_WIN64`\
64 bitlik kod iş alırken Düzenle ve Devam Windows kullanılamaz.

## <a name="remarks"></a>Açıklamalar
Bu numaralama yalnızca tarafından iç kullanım [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] içindir. Özel [bir bağlantı noktası sağlayıcı tarafından uygulanan GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) ve [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) yöntemleri her zaman dönüş gerçekleştirebilir. `E_NOTIMPL`

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg.idl

Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

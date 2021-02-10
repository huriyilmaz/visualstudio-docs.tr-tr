---
title: Haksız Blereason | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 384d71d6f88e8cd792585bb097594fa7b1e38c64
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99953753"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`**Düzenle ve devam et** 'in kullanılamayan nedenleri temsil eder.

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
Düzenleme ve devam etme işleminin neden kullanılamadığı belirli bir neden yoktur.

`ENCUN_INTEROP`\
Birlikte çalışma çağrısı sırasında Düzenle ve devam et kullanılamaz.

`ENCUN_SQLCLR`\
Düzenle ve devam et, ortak dil çalışma zamanını (CLR) kullanan bir SQL yordam çağrısı sırasında kullanılamaz.

`ENCUN_MINIDUMP`\
Bir mini döküm işlenirken Düzenle ve devam et kullanılamaz.

`ENCUN_EMBEDDED`\
Katıştırılmış kodu işlerken Düzenle ve devam et kullanılamaz.

`ENCUN_ATTACH`\
Oturum, hata ayıklayıcı tarafından başlatılmamış olarak eklendiği için Düzenle ve devam et kullanılamıyor.

`ENCUN_WIN64`\
64 bit Windows kodu işlenirken Düzenle ve devam et kullanılamaz.

## <a name="remarks"></a>Açıklamalar
Bu numaralandırma yalnızca tarafından iç kullanım içindir [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . Özel bir bağlantı noktası sağlayıcısı tarafından uygulanan [Getencavailablestate](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) ve [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) yöntemleri her zaman döndürmelidir `E_NOTIMPL` .

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. IDL

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

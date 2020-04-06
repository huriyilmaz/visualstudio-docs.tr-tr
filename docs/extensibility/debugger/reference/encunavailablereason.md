---
title: EncUnavailableReason | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- EncUnavailableReason
helpviewer_keywords:
- EncUnavailableReason enumeration
ms.assetid: c10aa4c0-d7e0-4de1-b8ff-7e050985eb12
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 28863549ab3eac96322530bc85c52697f20448c8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737160"
---
# <a name="encunavailablereason"></a>EncUnavailableReason
`This is for internal use only!`**Edit ve Continue'nin** kullanılamamasının nedenlerini gösterir.

## <a name="syntax"></a>Sözdizimi

```cpp
enum tagEncUnavailableReason {
    ENCUN_NONE,
    ENCUN_INTEROP,
    ENCUN_SQLCLR,
    ENCUN_MINIDUMP,
    ENCUN_EMBEDDED,
    ENCUN_ATTACH,
    ENCUN_WIN64
};
typedef enum tagEncUnavailableReason EncUnavailableReason;
```

```csharp
public enum EncUnavailableReason {
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
Edit ve Continue'nin kullanılamaması için özel bir neden yok.

`ENCUN_INTEROP`\
Bir InterOp araması sırasında Edit ve Continue kullanılamıyor.

`ENCUN_SQLCLR`\
Edit ve Continue, Ortak Dil Çalışma Zamanı (CLR) kullanan bir SQL yordam çağrısı sırasında kullanılamaz.

`ENCUN_MINIDUMP`\
Bir mini dökümü işlerken Edit ve Continue kullanılamıyor.

`ENCUN_EMBEDDED`\
Katıştırılmış kodu işlerken Edit ve Continue kullanılamıyor.

`ENCUN_ATTACH`\
Düzenleme ve Devam, oturum hata ayıklama tarafından başlatılmayan bağlı olduğundan kullanılamaz.

`ENCUN_WIN64`\
64 bit Windows kodunu işlerken Edit ve Continue kullanılamıyor.

## <a name="remarks"></a>Açıklamalar
Bu numaralandırma sadece [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]dahili kullanım içindir. Özel bir bağlantı noktası tedarikçisi tarafından uygulanan [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md) ve [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md) yöntemleri her zaman geri `E_NOTIMPL`dönmelidir.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.idl

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Numaralandırma](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)

- [DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)

- [GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)

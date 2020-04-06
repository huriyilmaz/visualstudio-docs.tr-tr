---
title: IDebugDocumentText2::GetText | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugDocumentText2::GetText
helpviewer_keywords:
- IDebugDocumentText2::GetText
ms.assetid: f8c15a58-da77-473e-a721-7a094e306c63
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 2429bdf3f09eff168210a7b835a9e506d74d63ea
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80731582"
---
# <a name="idebugdocumenttext2gettext"></a>IDebugDocumentText2::GetText
Belgedeki belirtilen konumdan metni alır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT GetText(
    TEXT_POSITION pos,
    ULONG         cMaxChars,
    WCHAR*        pText,
    ULONG*        pcNumChars
);
```

```csharp
int GetText(
    eumn_TEXT_POSITION pos,
    uint               cMaxChars,
    IntPtr             pText,
    out uint           pcNumChars
);
```

## <a name="parameters"></a>Parametreler
`pos`\
[içinde] Alınacak metnin konumunu gösteren [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md) bir yapı.

`cMaxChars`\
[içinde] Alınacak metnin en fazla karakter sayısı.

`pText`\
[içinde, dışarı] İstenilen metinle doldurulacak bir arabellek için bir işaretçi. Bu arabellek en az `cMaxChars` sayıda geniş karakter içerebilmelidir.

`pcNumChars`\
[çıkış] Gerçekte alınan karakter sayısını döndürür.

## <a name="return-value"></a>Dönüş Değeri
Başarılı olursa, `S_OK`döner; aksi takdirde, bir hata kodu döndürür.

## <a name="example"></a>Örnek
Bu örnek, bu yöntemin C#'dan nasıl çağrılabileceğini gösterir.

```csharp
using System.Runtime.Interop.Services;
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Debugger.Interop;

namespace Mynamespace
{
    class MyClass
    {
        string GetDocumentText(IDebugDocumentText2 pText, TEXT_POSITION pos)
        {
            string documentText = string.Empty;
            if (pText != null)
            {
                uint numLines = 0;
                uint numChars = 0;
                int hr;
                hr = pText.GetSize(ref numLines, ref numChars);
                if (ErrorHandler.Succeeded(hr))
                {
                    IntPtr buffer = Marshal.AllocCoTaskMem((int)numChars * sizeof(char));
                    uint actualChars = 0;
                    hr = pText.GetText(pos, numChars, buffer, out actualChars);
                    if (ErrorHandler.Succeeded(hr))
                    {
                        documentText = Marshal.PtrToStringUni(buffer, (int)actualChars);
                    }
                    Marshal.FreeCoTaskMem(buffer);
                }
            }
            return documentText;
        }
    }
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)
- [TEXT_POSITION](../../../extensibility/debugger/reference/text-position.md)

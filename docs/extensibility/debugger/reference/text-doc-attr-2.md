---
description: Bir belgenin özniteliklerini açıklar.
title: TEXT_DOC_ATTR_2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- TEXT_DOC_ATTR_2
helpviewer_keywords:
- TEXT_DOC_ATTR_2 enumeration
ms.assetid: 2333b33b-042b-4ac6-9ebe-e66f95f52f51
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ba69e22d55c589e758bebfe80e7836f970db19f3
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126634753"
---
# <a name="text_doc_attr_2"></a>TEXT_DOC_ATTR_2
Bir belgenin özniteliklerini açıklar.

## <a name="syntax"></a>Syntax

```cpp
typedef DWORD TEXT_DOC_ATTR_2;
const TEXT_DOC_ATTR_2 TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

```csharp
public const uint TEXT_DOC_ATTR_READONLY_2 = 0x00000001;
```

## <a name="members"></a>Üyeler
 `TEXT_DOC_ATTR_READONLY_2`\
 Belgenin salt okunur olduğunu gösterir.

## <a name="remarks"></a>Açıklamalar

> [!NOTE]
> Bu değer aslında C# için derlemede tanımlanmamıştır. Bunun yerine, tanımı kaynak dosyanıza kopyalamanız gerekir.

 [onUpdateDocumentAttributes yöntemine bağımsız değişken olarak](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md) geçirildi.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Listelemeler](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)
- [onUpdateDocumentAttributes](../../../extensibility/debugger/reference/idebugdocumenttextevents2-onupdatedocumentattributes.md)

---
description: Bir ifade değerlendiricisi (EE) hata ayıklayıcının çıkış penceresinde bir ileti görüntülemesini sağlar.
title: IDebugIDECallback | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: d0ef2072967aad5f2cd012283b0c6f4ac7b9b3be
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102172564"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Visual Studio 2015 ' de, değerlendiricileri ifadesi uygulama yöntemi kullanım dışıdır. CLR Expression değerlendiricileri 'ı uygulama hakkında daha fazla bilgi için lütfen bkz. [clr Expression değerlendiricileri](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [yönetilen ifade değerlendirici örneği](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample).

 Bir ifade değerlendiricisi (EE) hata ayıklayıcının çıkış penceresinde bir ileti görüntülemesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Bu geri çağırma, yönetilen hata ayıklama altyapısı tarafından uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklayıcının çıkış penceresine çıkış göndermek için bir ifade değerlendirici tarafından tüketilebilir.

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[DisplayMessage](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Belirtilen ileti dizesini hata ayıklayıcının çıkış penceresine gönderir.|

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

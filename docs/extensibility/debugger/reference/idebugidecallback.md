---
title: IDebugIDECallback | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugIDECallback interface
ms.assetid: 8d31adc0-1c44-4658-8d4f-f4b73e35f4a6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 585ff354cef9686097325ea4dea25cd08c4cbb1b
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80727833"
---
# <a name="idebugidecallback"></a>IDebugIDECallback
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bir ifade değerlendiricisinin (EE) hata ayıklayıcının çıkış penceresinde bir ileti görüntülemesini sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugIDECallback : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu geri çağırma yönetilen hata ayıklama altyapısı tarafından uygulanır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Hata ayıklayıcının çıkış penceresine çıktı göndermek için bir ifade değerlendirici tarafından tüketilebilir.

## <a name="methods"></a>Yöntemler
 Bu arabirim aşağıdaki yöntemi uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[Görüntülü İleti](../../../extensibility/debugger/reference/idebugidecallback-displaymessage.md)|Belirtilen ileti dizesini hata ayıklamanın çıkış penceresine gönderir.|

## <a name="requirements"></a>Gereksinimler
 Başlık: Ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

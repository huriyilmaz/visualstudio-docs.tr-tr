---
description: Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) işleme iliştirmekte veya işlemden ayrıldığı bir işlemi bilgilendirmesini sağlar.
title: IDebugProcessEx2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProcessEx2
helpviewer_keywords:
- IDebugProcessEx2 interface
ms.assetid: 44e309ba-1d6f-499b-aa7e-9b34858a6d57
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 4158f7f13f374e933bcf1ec64d40ecd16c85b40c
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122071908"
---
# <a name="idebugprocessex2"></a>IDebugProcessEx2
Bu arabirim, oturum hata ayıklama Yöneticisi 'nin (SDM) işleme iliştirmekte veya işlemden ayrıldığı bir işlemi bilgilendirmesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProcessEx2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
 Özel bir bağlantı noktası sağlayıcısı, bu arabirimi şu şekilde [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabirimiyle aynı nesne üzerinde uygular:

- Bir işleme bağlı oturumların izlenmesini destekleme

- Birden çok hata ayıklama altyapısı genelinde otomatik iliştirme desteği

  Özel bağlantı noktası sağlayıcısı, seçerse bu arabirimi uygulayabilir.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar

- SDM, [](/cpp/atl/queryinterface) `IDebugProcess2` Bu arabirimi almak Için bir arabirimdeki QueryInterface 'i çağırır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
 Aşağıdaki tabloda, yöntemleri gösterilmektedir `IDebugProcessEx2` .

|Yöntem|Açıklama|
|------------|-----------------|
|[İliştir](../../../extensibility/debugger/reference/idebugprocessex2-attach.md)|İşlemde bir oturumun hata ayıklaması olduğunu bildirir.|
|[Ayır](../../../extensibility/debugger/reference/idebugprocessex2-detach.md)|Bir oturumun işlemde artık hata ayıklalamadığını işleme bildirir.|
|[AddImplicitProgramNodes](../../../extensibility/debugger/reference/idebugprocessex2-addimplicitprogramnodes.md)|Hata ayıklama altyapısının listesi için program düğümleri ekler.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, SDM ve işlem arasında özeldir.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: Portprıv. h

 Ad alanı: Microsoft. VisualStudio. Debugger. Interop

 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)

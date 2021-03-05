---
description: Bu arabirim, hata ayıklama altyapısı (DE) veya özel bağlantı noktası sağlayıcılarının, programları hata ayıklama için kaydetmesini sağlar.
title: IDebugProgramPublisher2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: deac68ba693bd9e4f827fef5610e3c9d2c3c26f6
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102166976"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Bu arabirim, hata ayıklama altyapısı (DE) veya özel bağlantı noktası sağlayıcılarının, programları hata ayıklama için kaydetmesini sağlar.

## <a name="syntax"></a>Syntax

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Implemenonun notları
Visual Studio, birden çok işlemde hata ayıklama için görünür hale getirmek amacıyla hataları ayıklanan programları kaydetmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
`CoCreateInstance` `CLSID_ProgramPublisher` Bu arabirimi edınmek için com 'un işlevini çağırın (örneğe bakın). Bir DE veya özel bağlantı noktası sağlayıcısı, hata ayıklamakta olan programları temsil eden program düğümlerini kaydetmek için bu arabirimi kullanır.

## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler
Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|Bir program düğümünü DEs ve oturum hata ayıklama Yöneticisi (SDM) için kullanılabilir hale getirir.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Bir program düğümünü, artık kullanılabilir olmayacak şekilde kaldırır.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Bir programı DEs ve SDM için kullanılabilir hale getirir.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Artık kullanılamayan bir programı kaldırır.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Bir hata ayıklayıcının mevcut olduğunu belirten bir bayrak ayarlar.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, programlar ve program düğümlerinin kullanılabilir olmasını sağlar (yani "bunları" yayınlar) DEs ve oturum hata ayıklama Yöneticisi (SDM) tarafından kullanılmak üzere kullanır. Yayımlanmış programlar ve program düğümlerine erişmek için [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimini kullanın. Bu, Visual Studio 'Nun bir programın hata ayıklamakta olduğunu anlayabileceği tek yoldur.

## <a name="requirements"></a>Gereksinimler
Üst bilgi: msdbg. h

Ad alanı: Microsoft. VisualStudio. Debugger. Interop

Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, Program yayımcısının örneğini oluşturma ve program düğümünü kaydetme işlemlerinin nasıl yapılacağını gösterir. Bu, [Program düğümünü yayımlayan](/previous-versions/bb161795(v=vs.90))öğreticiden alınmıştır.

```cpp
// This is how m_srpProgramPublisher is defined in the class definition:
// CComPtr<IDebugProgramPublisher2> m_srpProgramPublisher.

void CProgram::Start(IDebugEngine2 * pEngine)
{
    m_spEngine = pEngine;

    HRESULT hr = m_srpProgramPublisher.CoCreateInstance(CLSID_ProgramPublisher);
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to create the program publisher: 0x%x.", hr);
        return;
    }

    // Register ourselves with the program publisher. Note that
    // CProgram implements the IDebgProgramNode2 interface, hence
    // the static cast on "this".
    hr = m_srpProgramPublisher->PublishProgramNode(
        static_cast<IDebugProgramNode2*>(this));
    if ( FAILED(hr) )
    {
        ATLTRACE("Failed to publish the program node: 0x%x.", hr);
        m_srpProgramPublisher.Release();
        return;
    }

    ATLTRACE("Added program node.\n");
}
```

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)

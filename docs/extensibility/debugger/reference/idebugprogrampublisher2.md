---
title: IDebugProgramPublisher2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProgramPublisher2
helpviewer_keywords:
- IDebugProgramPublisher2 interface
ms.assetid: b1d17f63-7146-4076-a588-034cfc6858b9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: b17f5bab02e49951eb1647af95641af807c44863
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80721529"
---
# <a name="idebugprogrampublisher2"></a>IDebugProgramPublisher2
Bu arabirim, hata ayıklama altyapısının (DE) veya özel bağlantı noktası tedarikçilerinin hata ayıklama için programları kaydetmesine olanak tanır.

## <a name="syntax"></a>Sözdizimi

```
IDebugProgramPublisher2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
Visual Studio, birden çok işlem arasında hata ayıklama için görünür hale getirmek için debugged olan programları kaydetmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
Bu arabirimi `CoCreateInstance` elde `CLSID_ProgramPublisher` etmek için COM'un işlevini arayın (Örnek'e bakın). De veya özel bağlantı noktası tedarikçisi, debugged olan programları temsil eden program düğümlerini kaydetmek için bu arabirimi kullanır.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
Bu arabirim aşağıdaki yöntemleri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[PublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogramnode.md)|DEs ve oturum hata ayıklama yöneticisi (SDM) için bir program düğümü kullanılabilir hale getirir.|
|[UnpublishProgramNode](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogramnode.md)|Artık kullanılamaması için program düğümlerini kaldırır.|
|[PublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-publishprogram.md)|Bir programı DEs ve SDM için kullanılabilir hale getirir.|
|[UnpublishProgram](../../../extensibility/debugger/reference/idebugprogrampublisher2-unpublishprogram.md)|Artık kullanılamaması için bir programı kaldırır.|
|[SetDebuggerPresent](../../../extensibility/debugger/reference/idebugprogrampublisher2-setdebuggerpresent.md)|Hata ayıklayanın bulunduğunu belirten bir bayrak ayarlar.|

## <a name="remarks"></a>Açıklamalar
Bu arabirim, programları ve program düğümlerini DEs ve oturum hata ayıklama yöneticisi (SDM) tarafından kullanılmak üzere kullanılabilir hale getirir (diğer bir şekilde bunları "yayımlar"). Yayımlanmış programlara ve program düğümlerine erişmek için [IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md) arabirimini kullanın. Visual Studio'nun bir programın debugged olduğunu fark edebildiği tek yol budur.

## <a name="requirements"></a>Gereksinimler
Üstbilgi: msdbg.h

Ad alanı: Microsoft.VisualStudio.Debugger.Interop

Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="example"></a>Örnek
Bu örnek, program yayımcısının anlık olarak nasıl kaydedilebildiğini ve bir program düğümünün nasıl kaydedilebildiğini gösterir. Bu Öğretici alınır, [Program Düğümü yayımlama](https://msdn.microsoft.com/library/d0100e02-4e2b-4e72-9e90-f7bc11777bae).

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

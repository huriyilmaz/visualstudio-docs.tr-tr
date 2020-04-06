---
title: IDebugObject | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject
helpviewer_keywords:
- IDebugObject interface
ms.assetid: 05cd8bf4-c9ee-4b49-b782-2263c33067d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 6801176964a47646f03091131e1be89cf63c97f8
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726307"
---
# <a name="idebugobject"></a>IDebugObject
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, bağlayıcının sembollerin ve ifadelerin değerlerini kapsüllemek için oluşturduğu bir nesneyi temsil eder.

## <a name="syntax"></a>Sözdizimi

```
IDebugObject : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bir ifade değerlendiricisi, bir nesneyi temsil etmek için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirim, ifade değerlendiricinin ayrıştırılmış ifadelerde kullandığı tüm nesnelerin taban sınıfıdır. [Bind](../../../extensibility/debugger/reference/idebugbinder-bind.md) yöntemine yapılan bir çağrıyla döndürülür. [QueryInterface](/cpp/atl/queryinterface) bu arabirimden daha özel arabirimler elde eder.

## <a name="methods-in-vtable-order"></a>Vtable Sıralı Yöntemler
 Aşağıdaki tabloda `IDebugObject`.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSize](../../../extensibility/debugger/reference/idebugobject-getsize.md)|Nesnenin boyutunu alır.|
|[GetValue](../../../extensibility/debugger/reference/idebugobject-getvalue.md)|Nesnenin değerini ardışık bayt serisi olarak alır.|
|[SetValue](../../../extensibility/debugger/reference/idebugobject-setvalue.md)|Nesnenin değerini ardışık bayt serisinden ayarlar.|
|[SetReferenceValue](../../../extensibility/debugger/reference/idebugobject-setreferencevalue.md)|Bu nesnenin başvuru değerini ayarlar.|
|[GetMemoryContext](../../../extensibility/debugger/reference/idebugobject-getmemorycontext.md)|Nesnenin değerinin adresini temsil eden bellek bağlamını alır.|
|[GetManagedDebugObject](../../../extensibility/debugger/reference/idebugobject-getmanageddebugobject.md)|Hata ayıklama altyapısının adres alanında yönetilen nesnenin bir kopyasını oluşturur.|
|[IsNullReference](../../../extensibility/debugger/reference/idebugobject-isnullreference.md)|Bu nesnenin null başvurusu olup olmadığını sına.|
|[IsEqual](../../../extensibility/debugger/reference/idebugobject-isequal.md)|Bir nesneyi bununla karşılaştırır.|
|[IsReadOnly](../../../extensibility/debugger/reference/idebugobject-isreadonly.md)|Bu nesnenin salt okunur olup olmadığını belirler.|
|[IsProxy](../../../extensibility/debugger/reference/idebugobject-isproxy.md)|Nesnenin saydam bir proxy olup olmadığını belirler.|

## <a name="remarks"></a>Açıklamalar
 İfade değerlendiricisi, ayrışma ağacındaki nesneleri temsil etmek için bu arabirimi taban sınıf olarak kullanır.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [GetElement](../../../extensibility/debugger/reference/idebugarrayobject-getelement.md)
- [Bağla](../../../extensibility/debugger/reference/idebugbinder-bind.md)

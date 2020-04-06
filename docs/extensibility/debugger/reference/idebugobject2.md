---
title: IDebugObject2 | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugObject2
helpviewer_keywords:
- IDebugObject2 interface
ms.assetid: ef640967-8adb-4793-994d-ae1736510891
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: e468b5a282ffb5466d57a3c9b1a37aa3ae8643ed
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80726081"
---
# <a name="idebugobject2"></a>IDebugObject2
> [!IMPORTANT]
> Visual Studio 2015'te ifade değerlendiricilerinin bu şekilde uygulanması amortismana uymaktadır. CLR ifade değerlendiricilerinin uygulanması hakkında bilgi için lütfen [CLR İfade Değerlendiriciler](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/CLR-Expression-Evaluators) ve [Yönetilen İfade Değerlendirici Örneği'ne](https://github.com/Microsoft/ConcordExtensibilitySamples/wiki/Managed-Expression-Evaluator-Sample)bakın.

 Bu arabirim, bir nesne hakkında ek bilgiler sağlar.

## <a name="syntax"></a>Sözdizimi

```
IDebugObject2 : IDebugObject
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 İfade değerlendiricisi, diğer adlar ve nesne hakkındaki bilgilere erişim için destek sunmak için bu arabirimi uygular.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bir [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimi [QueryInterface](/cpp/atl/queryinterface)kullanarak bu arabirimi elde edebilirsiniz. Ayrıca, [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md) bu arabirimi döndürür.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md) arabirimindeki yöntemlere ek `IDebugObject2` olarak, arabirim aşağıdakileri uygular:

|Yöntem|Açıklama|
|------------|-----------------|
|[GetBackingFieldForProperty](../../../extensibility/debugger/reference/idebugobject2-getbackingfieldforproperty.md)|Bu nesne tarafından temsil edilen özelliği destekleyen alanı veya değişkeni (varsa) alır.|
|[GetICorDebugValue](../../../extensibility/debugger/reference/idebugobject2-geticordebugvalue.md)|Bu nesnenin değerini temsil eden yönetilen kod nesnesini alır.|
|[CreateAlias](../../../extensibility/debugger/reference/idebugobject2-createalias.md)|Bu nesne için benzersiz bir kimlik oluşturur veya varolan bir diğer adı döndürür.|
|[GetAlias](../../../extensibility/debugger/reference/idebugobject2-getalias.md)|Varsa, bu nesneyle ilişkili diğer adı alır.|
|[GetField](../../../extensibility/debugger/reference/idebugobject2-getfield.md)|Bu nesnenin türünü alır.|
|[IsUserData](../../../extensibility/debugger/reference/idebugobject2-isuserdata.md)|Bu nesnenin kullanıcı verilerini temsil edip etmediğini belirler.|
|[IsEncOutdated](../../../extensibility/debugger/reference/idebugobject2-isencoutdated.md)|Edit ve Continue durumunun artık geçerli olup olmadığını belirler.<br /><br /> Özel bir ifade değerlendiricisi bu yöntemi uygulamaz (her zaman döndürülmelidir). `E_NOTIMPL`|

## <a name="remarks"></a>Açıklamalar
 Takma adlar hakkında bir tartışma için [IDebugAlias'a](../../../extensibility/debugger/reference/idebugalias.md) bakın.

## <a name="requirements"></a>Gereksinimler
 Üstbilgi: ee.h

 Ad alanı: Microsoft.VisualStudio.Debugger.Interop

 Montaj: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [İfade Değerlendirme Arabirimleri](../../../extensibility/debugger/reference/expression-evaluation-interfaces.md)
- [IDebugObject](../../../extensibility/debugger/reference/idebugobject.md)
- [IDebugAlias](../../../extensibility/debugger/reference/idebugalias.md)
- [GetObject](../../../extensibility/debugger/reference/idebugalias-getobject.md)

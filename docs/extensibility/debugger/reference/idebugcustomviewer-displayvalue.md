---
title: IDebugCustomViewer::DisplayValue | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: 32e444d0d6a30484f708d3001b95e7a71856edd5
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80732446"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Bu yöntem belirtilen değeri görüntülemek için çağrılır.

## <a name="syntax"></a>Sözdizimi

```cpp
HRESULT DisplayValue(
   HWND             hwnd,
   DWORD            dwID,
   IUnknown *       pHostServices,
   IDebugProperty3* pDebugProperty);
);
```

```csharp
int DisplayValue(
   IntPtr          hwnd,
   uint            dwID,
   object          pHostServices,
   IDebugProperty3 pDebugProperty
);
```

## <a name="parameters"></a>Parametreler
`hwnd`\
[içinde] Üst pencere

`dwID`\
[içinde] Birden fazla türü destekleyen özel görüntüleyenler için kimlik.

`pHostServices`\
[içinde] Saklı -dır. Her zaman hükümsüz olarak ayarlayın.

`pDebugProperty`\
[içinde] Görüntülenecek değeri almak için kullanılabilecek arabirim.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, `S_OK`döner; aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin gerekli pencereyi oluşturacağı, değeri göstereceği, girişi bekleyeceği ve arayanın geri dönmeden önce pencereyi kapatacağı için ekran "modal"dır. Bu, yöntemin çıktı için bir pencere oluşturmaktan kullanıcı girişi beklemeye, pencereyi yok etmeye kadar özelliğin değerini görüntülemenin tüm yönlerini işlemesi gerektiği anlamına gelir.

 Verilen [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) nesnesinin değerini değiştirmeyi desteklemek için, değer dize olarak ifade edilebiliyorsa [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) yöntemini kullanabilirsiniz. Aksi takdirde, `DisplayValue` `IDebugProperty3` arabirimi uygulayan aynı nesne üzerinde, bu yöntemi uygulayan ifade değerlendiriciye özel özel bir arabirim oluşturmak gerekir. Bu özel arabirim, rasgele bir boyutu veya karmaşıklığı verileri değiştirmek için yöntemler sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)

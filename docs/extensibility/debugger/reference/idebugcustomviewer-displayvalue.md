---
description: Belirtilen değeri görüntülemek için bu yöntem çağrılır.
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
dev_langs:
- CPP
- CSharp
ms.openlocfilehash: ab561a692b4f9fa96d8138079a68064558733792
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122079356"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Belirtilen değeri görüntülemek için bu yöntem çağrılır.

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
[in] Üst pencere

`dwID`\
[in] Birden fazla türü destekleyen özel görüntüleyicilerin kimliği.

`pHostServices`\
[in] Saklı -dır. Her zaman null olarak ayarlayın.

`pDebugProperty`\
[in] Görüntülenecek değeri almak için kullanılan arabirim.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa `S_OK` döndürür; aksi takdirde hata kodunu döndürür.

## <a name="remarks"></a>Açıklamalar
 Görüntüleme, bu yöntemin gerekli pencereyi oluşturması, değeri görüntülemesi, girişi beklemesi ve pencereyi kapatması için "kalıcıdır". Bu, yöntemin çıkış penceresi oluşturmaktan kullanıcı girişini beklemekten pencereyi yok etmeye kadar özelliğin değerini görüntülemenin tüm yönlerini işlemesi gerektiğini gösterir.

 Verilen [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) nesnesinde değerin değiştirilmesini desteklemek için [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) yöntemini kullanabilirsiniz; değer bir dize olarak ifade edildiyse. Aksi takdirde, arabirimi uygulayan aynı nesne üzerinde özel bir arabirim (bu yöntemi uygulayan ifade değerlendiricisine `DisplayValue` özel) oluşturmak `IDebugProperty3` gerekir. Bu özel arabirim, rastgele boyutta veya karmaşıklıkta verileri değiştirmek için yöntemler sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)

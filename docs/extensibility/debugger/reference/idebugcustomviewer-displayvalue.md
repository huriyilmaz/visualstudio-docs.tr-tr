---
description: Bu yöntem, belirtilen değeri göstermek için çağrılır.
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
ms.openlocfilehash: a3ff715cadd6499d74d3704faa9ad0e078d0838ee931b4fc6b68c4588fb45cc2
ms.sourcegitcommit: c72b2f603e1eb3a4157f00926df2e263831ea472
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/12/2021
ms.locfileid: "121377827"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Bu yöntem, belirtilen değeri göstermek için çağrılır.

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
'ndaki Üst pencere

`dwID`\
'ndaki Birden fazla türü destekleyen özel görüntüleyicilerin KIMLIĞI.

`pHostServices`\
'ndaki Ayrılamadı. Her zaman null olarak ayarlayın.

`pDebugProperty`\
'ndaki Görüntülenecek değeri almak için kullanılabilecek arabirim.

## <a name="return-value"></a>Dönüş Değeri
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.

## <a name="remarks"></a>Açıklamalar
 Bu yöntemin gerekli pencereyi oluşturması, değeri görüntülemesi, giriş için beklemesi ve tüm arayana dönmeden önce pencereyi kapatması için ekran "kalıcı" olur. Bu yöntem, yöntemin, çıkış için pencere oluşturma işleminin, pencereyi yok etmek için, Kullanıcı girişi beklemek üzere, özelliğin değerini görüntülemenin tüm yönlerini işlemesi gerektiği anlamına gelir.

 Verilen [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) nesnesindeki değerin değiştirilmesini desteklemek için, değer bir dize olarak Ifade edilebilir [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) yöntemini kullanabilirsiniz. Aksi takdirde, bu yöntemi uygulayan ifade değerlendiricisi için özel bir arabirim oluşturmak gerekir — `DisplayValue` arabirimi uygulayan nesne üzerinde `IDebugProperty3` . Bu özel arabirim, rastgele bir boyut veya karmaşıklık verilerinin değiştirilmesini sağlayacak yöntemler sağlar.

## <a name="see-also"></a>Ayrıca bkz.
- [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)
- [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)
- [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)

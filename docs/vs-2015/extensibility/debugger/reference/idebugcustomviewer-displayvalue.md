---
title: IDebugCustomViewer::D isplayValue | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugCustomViewer::DisplayValue
helpviewer_keywords:
- IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: 12
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: bda4c60e9164ae195c0e3ba49893b1a818c66f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62421378"
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu yöntem, belirtilen değeri göstermek için çağrılır.  
  
## <a name="syntax"></a>Söz dizimi  
  
```cpp#  
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
  
#### <a name="parameters"></a>Parametreler  
 `hwnd`  
 'ndaki Üst pencere  
  
 `dwID`  
 'ndaki Birden fazla türü destekleyen özel görüntüleyicilerin KIMLIĞI.  
  
 `pHostServices`  
 'ndaki Ayrılamadı. Her zaman null olarak ayarlayın.  
  
 `pDebugProperty`  
 'ndaki Görüntülenecek değeri almak için kullanılabilecek arabirim.  
  
## <a name="return-value"></a>Dönüş Değeri  
 Başarılı olursa, döndürür `S_OK` ; Aksi takdirde hata kodu döndürür.  
  
## <a name="remarks"></a>Açıklamalar  
 Bu yöntemin gerekli pencereyi oluşturması, değeri görüntülemesi, giriş için beklemesi ve tüm arayana dönmeden önce pencereyi kapatması için ekran "kalıcı" olur. Bu yöntem, yöntemin, çıkış için pencere oluşturma işleminin, pencereyi yok etmek için, Kullanıcı girişi beklemek üzere, özelliğin değerini görüntülemenin tüm yönlerini işlemesi gerektiği anlamına gelir.  
  
 Verilen [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) nesnesindeki değerin değiştirilmesini desteklemek için, değer bir dize olarak Ifade edilebilir [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) yöntemini kullanabilirsiniz. Aksi takdirde, bu yöntemi uygulayan ifade değerlendiricisi için özel bir arabirim oluşturmak gerekir — `DisplayValue` arabirimi uygulayan nesne üzerinde `IDebugProperty3` . Bu özel arabirim, rastgele bir boyut veya karmaşıklık verilerinin değiştirilmesini sağlayacak yöntemler sağlar.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)

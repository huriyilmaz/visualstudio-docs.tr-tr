---
description: Bu arabirim, programla ilgili arabirimleri işlem sınırları arasında sıralar.
title: IDebugProviderProgramNode2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- IDebugProviderProgramNode2
helpviewer_keywords:
- IDebugProviderProgramNode2
ms.assetid: f0bca1cc-afbe-44cf-b5aa-d078aa685d24
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 43a66e927d2a1d2e1afc84688bb3a36451fffecc
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070998"
---
# <a name="idebugproviderprogramnode2"></a>IDebugProviderProgramNode2
Bu arabirim, programla ilgili arabirimleri işlem sınırları arasında sıralar.

## <a name="syntax"></a>Syntax

```
IDebugProviderProgramNode2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapısı (DE), bu arabirimi işlem sınırları arasında sıralama arabirimlerini desteklemek için [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md) uygulayan aynı nesnede uygulamaya almaktadır.

## <a name="notes-for-callers"></a>Arayanlar İçin Notlar
 Bu arabirimi almak için bir arabirimde [QueryInterface](/cpp/atl/queryinterface) `IDebugProgramNode2` çağrısı yapmak. Bu arabirim alınamazsa, DE arabirimlerin sıralarını desteklemez.

## <a name="methods-in-vtable-order"></a>Vtable sırasına göre yöntemler
 Bu arabirim aşağıdaki yöntemi kullanır:

|Yöntem|Açıklama|
|------------|-----------------|
|[UnmarshalDebuggeeInterface](../../../extensibility/debugger/reference/idebugproviderprogramnode2-unmarshaldebuggeeinterface.md)|İşlem sınırları arasında belirtilen arabirimi alır.|

## <a name="remarks"></a>Açıklamalar
 Bu arabirim, DE hata ayıklaması yapılan programdan ayrı bir işlem alanı içinde çalıştırıldıklarında uygulanır: örneğin, DE hata ayıklaması yapılan programın işlem alanı yerine Visual Studio işlem alanı içinde çalıştırıldı olduğunda.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

## <a name="see-also"></a>Ayrıca bkz.
- [Temel Arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)
- [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)

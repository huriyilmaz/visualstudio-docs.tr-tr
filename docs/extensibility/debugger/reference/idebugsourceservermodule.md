---
description: Bir PDB dosyasında bulunan kaynak sunucu bilgilerini temsil eder.
title: IDebugSourceServerModule | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugSourceServerModule interface
ms.assetid: 38213060-451d-46e6-8b4a-efc123e01a2c
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d8271fe7d639ab937f3b3a51ff66b86649b90693
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122070911"
---
# <a name="idebugsourceservermodule"></a>IDebugSourceServerModule
Bir PDB dosyasında bulunan kaynak sunucu bilgilerini temsil eder.

## <a name="syntax"></a>Syntax

```
IDebugSourceServerModule : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Bu arabirim hata ayıklayıcı altyapıları tarafından uygulanır ve hata ayıklayıcı kullanıcı arabirimi tarafından kullanılır.

## <a name="methods"></a>Yöntemler
 Aşağıdaki tabloda yöntemlerini `IDebugSourceServerModule` gösterir.

|Yöntem|Açıklama|
|------------|-----------------|
|[GetSourceServerData](../../../extensibility/debugger/reference/idebugsourceservermodule-getsourceserverdata.md)|Kaynak sunucu bilgilerini içeren bir diziyi döndürür.|

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

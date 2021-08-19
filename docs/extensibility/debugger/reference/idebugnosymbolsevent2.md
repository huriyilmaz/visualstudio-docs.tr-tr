---
description: Kullanıcıya Visual Studio yürütülebilir dosya için sembollerin bulunamayy olduğunu uyarısı için hata ayıklayıcı kullanıcı arabirimini gönderir.
title: IDebugNoSymbolsEvent2 | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- IDebugNoSymbolsEvent2 interface
ms.assetid: f6fb6388-47f6-4385-9ad5-95d62f9a7592
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: d3f2eed2c6ea1e50ede7ec539e9ecc80afec2b7b
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122160224"
---
# <a name="idebugnosymbolsevent2"></a>IDebugNoSymbolsEvent2
Hata [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ayıklayıcısı kullanıcı arabirimine, başlatılan yürütülebilir dosya için sembollerin bulunamay tarafından uyarılmaya yönelik sinyaller gönderir.

## <a name="syntax"></a>Syntax

```
IDebugNoSymbolsEvent2 : IUnknown
```

## <a name="notes-for-implementers"></a>Uygulayıcılar için Notlar
 Hata ayıklama altyapıları tarafından uygulanır ve hata ayıklayıcı kullanıcı [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] arabirimi tarafından tüketilir.

## <a name="requirements"></a>Gereksinimler
 Üst bilgi: Msdbg.h

 Ad Alanı: Microsoft.VisualStudio.Debugger.Interop

 Derleme: Microsoft.VisualStudio.Debugger.Interop.dll

---
description: Bu göreve kayıtlı alt görevlerin listesi.
title: m_children Alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 311ab164551e46fbe1c30b5a6045a7993a900a67
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112901376"
---
# <a name="m_children-field"></a>m_children alanı
Bu göreve kayıtlı alt görevlerin listesi.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

 Bu iç üyeye .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Açıklamalar
 Görev çalışırken, bu diziye yalnızca görevi yürüten iş parçacığı erişmeli.

 Görev tamamlanırsa, diğer iş parçacıkları bu alana herhangi bir şey ekleme veya bu alandan herhangi bir şey kaldırmamaları sürece bu alana erişebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.
- [ContingentProperties sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)

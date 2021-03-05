---
description: Bu görevle kaydedilen alt görevlerin listesi.
title: m_children alanı | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 5aaf29d76a7bbd81a416c86360f315bc5c09b76c
ms.sourcegitcommit: 4b323a8a8bfd1a1a9e84f4b4ca88fa8da690f656
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/05/2021
ms.locfileid: "102158875"
---
# <a name="m_children-field"></a>m_children alanı
Bu görevle kaydedilen alt görevlerin listesi.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Bütünleştirilmiş kod:** mscorlib ( *mscorlib.dll*)

 Bu iç üyeye .NET Framework erişeolmadığınızdan, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.

## <a name="syntax"></a>Syntax

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Açıklamalar
 Görev çalışırken, yalnızca görevi yürüten iş parçacığının bu diziye erişmesi gerekir.

 Görev tamamlanırsa, diğer iş parçacıkları buna hiçbir şey eklemedikleri veya bundan herhangi bir şeyi kaldırabileceği sürece bu alana erişebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [Kıgentproperties sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)

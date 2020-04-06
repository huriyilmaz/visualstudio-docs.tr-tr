---
title: m_children Alanı | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 07933fd4c9f359e72714600abdf8b4ee29268f84
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738431"
---
# <a name="m_children-field"></a>m_children alanı
Bu göreve kayıtlı alt görevlerin listesi.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

 Bu iç üyeye .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

```csharp
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children
```

## <a name="remarks"></a>Açıklamalar
 Görev çalışırken, yalnızca görevi yürüten iş parçacığı bu diziye erişmelidir.

 Görev tamamlanırsa, diğer iş parçacıkları bu alana bir şey eklemedikleri veya ondan bir şey kaldırmadıkları sürece erişebilir.

## <a name="see-also"></a>Ayrıca bkz.
- [ContingentProperties sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)

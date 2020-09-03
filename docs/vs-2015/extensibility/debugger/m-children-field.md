---
title: m_children alanı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_children field, ContingentProperties class [.NET Framework debug engines]
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 13
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 749b7a8da2cbdf8377e7f2e1fcb39787e2f42303
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149055"
---
# <a name="m_children-field"></a>m_children Alanı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu görevle kaydedilen alt görevlerin listesi.  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyeye .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Görev çalışırken, yalnızca görevi yürüten iş parçacığının bu diziye erişmesi gerekir.  
  
 Görev tamamlanırsa, diğer iş parçacıkları buna hiçbir şey eklemedikleri veya bundan herhangi bir şeyi kaldırabildiği sürece bu alana erişebilir.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [ContingentProperties Sınıfı](../../extensibility/debugger/contingentproperties-class-internal-members.md)

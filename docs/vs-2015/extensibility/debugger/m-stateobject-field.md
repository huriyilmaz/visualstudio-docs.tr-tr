---
title: m_stateObject alanı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- m_stateObject field, Task class [.NET Framework debug engines]
ms.assetid: 68c54b22-3e1c-4031-b9c7-b972c519d8a0
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 8e9cfc6f689504bef2a8366f90282641d1e9e105
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68149049"
---
# <a name="m_stateobject-field"></a>m_stateObject Alanı
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Eylemin kullanacağı verileri temsil eden nesne.  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyeye .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.field assembly object m_stateObject  
```  
  
## <a name="remarks"></a>Açıklamalar  
 Bu, `state` <xref:System.Threading.Tasks.Task.%23ctor%2A> kurucudaki parametredir. Ayrıca, özelliği için de yedekleme alanıdır <xref:System.Threading.Tasks.Task.AsyncState%2A?displayProperty=fullName> .  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Task Sınıfı](../../extensibility/debugger/task-class-internal-members.md)

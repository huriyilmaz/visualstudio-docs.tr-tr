---
title: AsyncTaskMethodBuilder &lt; TResult &gt; yapısı-iç Üyeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- AsyncTaskMethodBuilder<TResult> structure [.NET Framework debug engines]
- debug engines, AsyncTaskMethodBuilder<TResult> structure [.NET Framework]
ms.assetid: 17ebc340-8170-4aff-bf54-dc4548c83632
caps.latest.revision: 5
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 7e4999b71ae8f654aa3d362ba16c6cf5bc6574da
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "68182260"
---
# <a name="asynctaskmethodbuilderlttresultgt-structure---internal-members"></a>AsyncTaskMethodBuilder &lt; TResult &gt; yapısı-iç Üyeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu konu, sınıfının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> . Bu sınıf hakkında genel bilgi için <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601> başvuru konusuna bakın.  
  
 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder`1<TResult>  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>İç Üyeler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-tresult-objectidfordebugger-property.md)|Bu oluşturucuyu hata ayıklayıcıya benzersiz bir şekilde tanımlamak için kullanılabilecek bir nesne alır.|  
|[m_task alanı](../../extensibility/debugger/asynctaskmethodbuilder-tresult-m-task-field.md)|Geç tarafından başlatılan oluşturulmuş görevi temsil eder.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder%601>   
 [.NET Framework için Paralel Uzantı Dahili Bileşenleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

---
title: AsyncTaskMethodBuilder yapısı-dahili Üyeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, AsyncTaskMethodBuilder structure [.NET Framework]
- AsyncTaskMethodBuilder structure [.NET Framework debug engines]
ms.assetid: f32f5857-7ef8-45fd-8b5a-7f644eb98b11
caps.latest.revision: 6
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 0bfe640654c9de7daac9096aa4d75f5492a8a278
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62555918"
---
# <a name="asynctaskmethodbuilder-structure---internal-members"></a>AsyncTaskMethodBuilder Yapısı - Dahili Üyeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu konu, sınıfının iç üyelerini açıklar <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> . Bu sınıf hakkında genel bilgi için <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder> başvuru konusuna bakın.  
  
 **Ad alanı:**<xref:System.Runtime.CompilerServices?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
.class public sequential ansi sealed beforefieldinit System.Runtime.CompilerServices.AsyncTaskMethodBuilder  
       extends System.ValueType  
       implements System.Runtime.CompilerServices.IAsyncMethodBuilder  
```  
  
## <a name="internal-members"></a>İç Üyeler  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[ObjectIdForDebugger özelliği](../../extensibility/debugger/asynctaskmethodbuilder-objectidfordebugger-property.md)|Bu oluşturucuyu hata ayıklayıcıya benzersiz bir şekilde tanımlamak için kullanılabilecek bir nesne alır.|  
|[m_builder alanı](../../extensibility/debugger/asynctaskmethodbuilder-m-builder-field.md)|Bu genel olmayan örneğin temsilcilerin bulunduğu genel Oluşturucu nesnesini temsil eder.|  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Runtime.CompilerServices.AsyncTaskMethodBuilder>   
 [.NET Framework için Paralel Uzantı Dahili Bileşenleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

---
title: Görev Sınıfı - İç Üyeler | Microsoft Docs
description: Özel bir hata ayıklayıcı uygulamanıza yardımcı olan System.Threading.Tasks.Task sınıfının iç üyeleri hakkında bilgi edinebilirsiniz.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 37691714d0168594b61a1a3849f7b65264e9999e
ms.sourcegitcommit: bab002936a9a642e45af407d652345c113a9c467
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 06/25/2021
ms.locfileid: "112902897"
---
# <a name="task-class---internal-members"></a>Görev sınıfı - iç üyeler
Bu makalede, özel bir hata ayıklayıcı <xref:System.Threading.Tasks.Task?displayProperty=fullName> uygulamanıza yardımcı olan sınıfının iç üyeleri açıklanmıştır. Bu sınıf hakkında genel bilgi için başvuru <xref:System.Threading.Tasks.Task> makalesine bakın.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Derleme:** mscorlib *(mscorlib.dll*)

 Bu iç üyelere .NET Framework erişe .NET Framework Ortak Ara Dil (CIL) içinde sağlanmıştır.

## <a name="syntax"></a>Syntax

```csharp
.class public auto ansi System.Threading.Tasks.Task
       extends System.Object
       implements System.Threading.IThreadPoolWorkItem,
                  System.IAsyncResult,
                  System.IDisposable,
                  System.Threading.ICancelableOperation
```

## <a name="members"></a>Üyeler

### <a name="methods"></a>Yöntemler

|Ad|Açıklama|
|----------|-----------------|
|[SetNotificationForWaitCompletion Metodu](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|Durum biti kümelerini TASK_STATE_WAIT_COMPLETION_NOTIFICATION veya temizler.|
|[NotifyDebuggerOfWaitCompletion Metodu](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Hata ayıklayıcı tarafından kesme noktası hedefi olarak kullanılan yer tutucu yöntemi.|

### <a name="fields"></a>Alanlar

|Ad|Açıklama|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|Nesnesinde yürütülecek kodu temsil eden <xref:System.Threading.Tasks.Task> temsilci.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Nesnenin ek özelliklerini <xref:System.Threading.Tasks.Task> depolar.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Üst özelliğin <xref:System.Threading.Tasks.Task?displayProperty=fullName> destek alanı.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Nesnenin geçerli durumuyla ilgili bilgileri <xref:System.Threading.Tasks.Task> depolar.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Eylem tarafından kullanılacak verileri temsil eden bir nesne.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|özelliği için backing <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> alanı.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Bir nesne için bir sonraki kullanılabilir <xref:System.Threading.Tasks.Task> tanımlayıcı.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Görevin çalışma durumuna ulaşmadan önce iptal edildiğini veya görevin iptalini onaylamış ve özel durum olmadan tamamlamış olduğunu gösterir.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Görevin çalışıyor olduğunu gösterir.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|İşlenemeyen bir özel durum nedeniyle görevin tamamlandıktan sonra olduğunu gösterir.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Görevin yürütmeyi başarıyla tamamlamış olduğunu gösterir.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Görevin temsilcisini yürütmeyi tamam harcadığını ve ekli alt görevlerin bitip bitip bitenin örtülü olarak beklediğini gösterir.|

## <a name="remarks"></a>Açıklamalar
 Aşağıdaki iç yöntemler, kod yürütme girişine işaret eden bir hata ayıklayıcı altyapısı <xref:System.Threading.Tasks.Task> için yararlıdır:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET Framework için paralel uzantı iç .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

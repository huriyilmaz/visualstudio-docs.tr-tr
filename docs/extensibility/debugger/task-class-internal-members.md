---
title: Görev Sınıfı - Dahili Üyeler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: dcf278c0248b344cea4be7cf161ecc91581f5f2e
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80712744"
---
# <a name="task-class---internal-members"></a>Görev sınıfı - dahili üyeler
Bu makalede, özel bir <xref:System.Threading.Tasks.Task?displayProperty=fullName> hata ayıklama uygulamanıza yardımcı sınıfın iç üyeleri açıklanır. Bu sınıf hakkında genel bilgi <xref:System.Threading.Tasks.Task> için başvuru makalesine bakın.

 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>

 **Montaj:** mscorlib *(mscorlib.dll*olarak)

 Bu dahili üyelere .NET Framework'den erişemediğinizden, aşağıdaki sözdizimi Ortak Ara Dil 'de (CIL) sağlanır.

## <a name="syntax"></a>Sözdizimi

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

|Adı|Açıklama|
|----------|-----------------|
|[SetNotificationForWaitCompletion Metodu](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|TASK_STATE_WAIT_COMPLETION_NOTIFICATION durum bitini ayarlar veya temizler.|
|[NotifyDebuggerOfWaitCompletion Metodu](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Yer tutucu yöntemi hata ayıklama tarafından kesme noktası hedefi olarak kullanılır.|

### <a name="fields"></a>Alanlar

|Adı|Açıklama|
|----------|-----------------|
|[m_action](../../extensibility/debugger/m-action-field.md)|<xref:System.Threading.Tasks.Task> Nesnede yürütülecek kodu temsil eden temsilci.|
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Nesnenin <xref:System.Threading.Tasks.Task> ek özelliklerini depolar.|
|[m_parent](../../extensibility/debugger/m-parent-field.md)|<xref:System.Threading.Tasks.Task?displayProperty=fullName> Ana mülkün destek alanı.|
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|<xref:System.Threading.Tasks.Task> Nesnenin geçerli durumu yla ilgili bilgileri depolar.|
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Eylem tarafından kullanılacak verileri temsil eden bir nesne.|
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|<xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> Mülkün destek alanı.|
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Bir <xref:System.Threading.Tasks.Task> nesne için kullanılabilir bir sonraki tanımlayıcı.|
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Görevin çalışan duruma ulaşmadan önce iptal edildiğini veya görevin iptalini onayladığını ve istisnasız tamamlandığını gösterir.|
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Görevin çalıştığını gösterir.|
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|Ele alınamayan bir özel durum nedeniyle görevin tamamlandığını gösterir.|
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Görevin yürütmeyi başarıyla tamamladığını gösterir.|
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Görevin temsilcisini yürütmeyi tamamladığını ve dolaylı olarak eklenmiş alt görevlerin tamamlanmasını beklediğini gösterir.|

## <a name="remarks"></a>Açıklamalar
 Kod yürütme girişini işaretlediğinden, aşağıdaki dahili yöntemler <xref:System.Threading.Tasks.Task> hata ayıklayıcı altyapısı için yararlıdır:

- `Execute`

- `ExecuteEntry`

- `ExecuteWithThreadLocal`

- `Finish`

- `InnerInvoke`

- `InternalWait`

## <a name="see-also"></a>Ayrıca bkz.
- <xref:System.Threading.Tasks.Task?displayProperty=fullName>
- [.NET Framework için paralel uzantı dahili](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

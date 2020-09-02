---
title: Görev sınıfı-Iç Üyeler | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, Task class [.NET Framework]
- Task class [.NET Framework debug engines]
ms.assetid: 28e47c3b-9323-424a-80ac-6cc3bf19e09b
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: ef0cd907c25a90ee90e3ed23a773d0ae8ba0ce1f
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64790300"
---
# <a name="task-class---internal-members"></a>Görev Sınıfı - Dahili Üyeler
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bu konu, <xref:System.Threading.Tasks.Task?displayProperty=fullName> özel bir hata ayıklayıcı uygulamanıza yardımcı olan sınıfın iç üyelerini açıklar. Bu sınıf hakkında genel bilgi için <xref:System.Threading.Tasks.Task> başvuru konusuna bakın.  
  
 **Ad alanı:**<xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Bütünleştirilmiş kod:** mscorlib (mscorlib.dll)  
  
 Bu iç üyelere .NET Framework erişemediği için, ortak ara dil (CıL) içinde aşağıdaki sözdizimi sunulmaktadır.  
  
## <a name="syntax"></a>Syntax  
  
```  
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
|[SetNotificationForWaitCompletion Metodu](../../extensibility/debugger/setnotificationforwaitcompletion-method.md)|TASK_STATE_WAIT_COMPLETION_NOTIFICATION durum bitini ayarlar veya temizler.|  
|[NotifyDebuggerOfWaitCompletion Metodu](../../extensibility/debugger/notifydebuggerofwaitcompletion-method.md)|Hata ayıklayıcı tarafından bir kesme noktası hedefi olarak kullanılan yer tutucu yöntemi.|  
  
### <a name="fields"></a>Alanlar  
  
|Ad|Açıklama|  
|----------|-----------------|  
|[m_action](../../extensibility/debugger/m-action-field.md)|Nesnede yürütülecek kodu temsil eden temsilci <xref:System.Threading.Tasks.Task> .|  
|[m_contingentProperties](../../extensibility/debugger/m-contingentproperties-field.md)|Nesnenin ek özelliklerini depolar <xref:System.Threading.Tasks.Task> .|  
|[m_parent](../../extensibility/debugger/m-parent-field.md)|Üst özellik için yedekleme alanı <xref:System.Threading.Tasks.Task?displayProperty=fullName> .|  
|[m_stateFlags](../../extensibility/debugger/m-stateflags-field.md)|Nesnenin geçerli durumu hakkında bilgi depolar <xref:System.Threading.Tasks.Task> .|  
|[m_stateObject](../../extensibility/debugger/m-stateobject-field.md)|Eylem tarafından kullanılacak verileri temsil eden nesne.|  
|[m_taskId](../../extensibility/debugger/m-taskid-field.md)|Özelliği için yedekleme alanı <xref:System.Threading.Tasks.Task.Id%2A?displayProperty=fullName> .|  
|[s_taskIdCounter](../../extensibility/debugger/s-taskidcounter-field.md)|Bir nesne için bir sonraki kullanılabilir tanımlayıcı <xref:System.Threading.Tasks.Task> .|  
|[TASK_STATE_CANCELED](../../extensibility/debugger/task-state-canceled-field.md)|Görevin çalışma durumuna erişmeden önce iptal edildiğini veya görevin iptalini kabul edildiğini ve özel durum olmadan tamamlandığını gösterir.|  
|[TASK_STATE_EXECUTED](../../extensibility/debugger/task-state-executed-field.md)|Görevin çalıştığını gösterir.|  
|[TASK_STATE_FAULTED](../../extensibility/debugger/task-state-faulted-field.md)|İşlenmemiş bir özel durum nedeniyle görevin tamamlandığını gösterir.|  
|[TASK_STATE_RAN_TO_COMPLETION](../../extensibility/debugger/task-state-ran-to-completion-field.md)|Görevin yürütmenin başarıyla tamamlandığını gösterir.|  
|[TASK_STATE_WAITING_ON_CHILDREN](../../extensibility/debugger/task-state-waiting-on-children-field.md)|Görevin, temsilcisini yürütmeyi bitirdiğini ve ekli alt görevlerin tamamlanmasını örtük olarak beklediğini belirtir.|  
  
## <a name="remarks"></a>Açıklamalar  
 Aşağıdaki iç Yöntemler, kod yürütmeye giriş işaretini işaretlerse bir hata ayıklayıcı altyapısı için yararlıdır <xref:System.Threading.Tasks.Task> :  
  
- `Execute`  
  
- `ExecuteEntry`  
  
- `ExecuteWithThreadLocal`  
  
- `Finish`  
  
- `InnerInvoke`  
  
- `InternalWait`  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 <xref:System.Threading.Tasks.Task?displayProperty=fullName>   
 [.NET Framework için Paralel Uzantı Dahili Bileşenleri](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)

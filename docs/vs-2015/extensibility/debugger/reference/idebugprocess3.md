---
title: IDebugProcess3 | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: reference
f1_keywords:
- IDebugProcess3
helpviewer_keywords:
- IDebugProcess3 interface
ms.assetid: 7bd6b952-cf34-4e66-b8f6-d472dac3748f
caps.latest.revision: 25
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 490d1e5f8048188e442f0113f8cf91bafe2344ed
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "65675397"
---
# <a name="idebugprocess3"></a>IDebugProcess3
[!INCLUDE[vs2017banner](../../../includes/vs2017banner.md)]

Bu arabirim çalışan bir işlemi ve programlarını temsil eder. Bu arabirim, [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabirimindeki çeşitli yöntemlerin yerini alacak şekilde bulunur. İşlemdeki tüm programlar üzerinde denetim sağlar.  
  
> [!NOTE]
> [Devam etme](../../../extensibility/debugger/reference/idebugprogram2-continue.md), [yürütme](../../../extensibility/debugger/reference/idebugprogram2-execute.md)ve [adım](../../../extensibility/debugger/reference/idebugprogram2-step.md) yöntemleri kullanım dışıdır ve artık kullanılmamalıdır. Bunun yerine arabirim üzerinde ilgili yöntemleri kullanın `IDebugProcess3` .  
  
## <a name="syntax"></a>Syntax  
  
```  
IDebugProcess3 : IDebugProcess2  
```  
  
## <a name="notes-for-implementers"></a>Implemenonun notları  
 Bu arabirim, programları bir grup olarak yönetmek için özel bir bağlantı noktası sağlayıcısı tarafından uygulanır. Programlar bir grup olarak yönetildiğinde, yürütmesini denetleyebilir ve bir ifade değerlendirici için dil oluşturabilirsiniz. Bu arabirimin bağlantı noktası sağlayıcısı tarafından uygulanması gerekir.  
  
## <a name="notes-for-callers"></a>Arayanlar İçin Notlar  
 Bu arabirim öncelikle bu işlemde tanımlanan bir program grubuyla etkileşim kurmak için oturum hata ayıklama Yöneticisi (SDM) tarafından çağrılır.  
  
 Bu arabirimi almak için bir [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md) arabiriminde [QueryInterface](https://msdn.microsoft.com/library/62fce95e-aafa-4187-b50b-e6611b74c3b3) 'i çağırın.  
  
## <a name="methods-in-vtable-order"></a>Vtable sırasındaki Yöntemler  
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)öğesinden devralınan yöntemlere ek olarak `IDebugProcess3` aşağıdaki yöntemleri uygular.  
  
|Yöntem|Açıklama|  
|------------|-----------------|  
|[Devam et](../../../extensibility/debugger/reference/idebugprocess3-continue.md)|Bir işlemden yürütmeye devam eder.|  
|[Yürütme](../../../extensibility/debugger/reference/idebugprocess3-execute.md)|Bir işlemin yürütülmesine başlar.|  
|[Adım](../../../extensibility/debugger/reference/idebugprocess3-step.md)|İşlemler, işlemde bir yönerge veya ifade iletir.|  
|[GetDebugReason](../../../extensibility/debugger/reference/idebugprocess3-getdebugreason.md)|İşlemin hata ayıklama için başlatılmasının nedenini alır.|  
|[SetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-sethostingprocesslanguage.md)|Hata ayıklama altyapısının uygun ifade değerlendiricisi 'nı yükleyebilmesi için barındırma dilini ayarlar.|  
|[GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)|Bu işlem için şu anda ayarlanmış olan dili alır.|  
|[DisableENC](../../../extensibility/debugger/reference/idebugprocess3-disableenc.md)|Bu işlem için Düzenle ve devam et (ENC) işlemini devre dışı bırakır.<br /><br /> Özel bir bağlantı noktası sağlayıcısı bu yöntemi uygulamaz (her zaman döndürmelidir `E_NOTIMPL` ).|  
|[GetENCAvailableState](../../../extensibility/debugger/reference/idebugprocess3-getencavailablestate.md)|Bu işlem için ENC durumunu alın.<br /><br /> Özel bir bağlantı noktası sağlayıcısı bu yöntemi uygulamaz (her zaman döndürmelidir `E_NOTIMPL` ).|  
|[GetEngineFilter](../../../extensibility/debugger/reference/idebugprocess3-getenginefilter.md)|Kullanılabilir hata ayıklama motorları için benzersiz tanımlayıcıların dizisini alır.|  
  
## <a name="requirements"></a>Gereksinimler  
 Üst bilgi: msdbg. h  
  
 Ad alanı: Microsoft. VisualStudio. Debugger. Interop  
  
 Bütünleştirilmiş kod: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Çekirdek arabirimler](../../../extensibility/debugger/reference/core-interfaces.md)   
 [IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)   
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)

---
title: Bir başlatma Işleminden sonra iliştirme | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
caps.latest.revision: 15
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 693cf6d746f51862415f2f30e46d48a998047f14
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "64835336"
---
# <a name="attaching-after-a-launch"></a>Başlatmadan Sonra Ekleme
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Bir program başlatıldıktan sonra, hata ayıklama oturumu, söz konusu programa hata ayıklama altyapısını (DE) eklemeye hazırdır.  
  
## <a name="design-decisions"></a>Tasarım Kararları  
 İletişim, paylaşılan bir adres alanında daha kolay olduğundan, hata ayıklama oturumu ile DE arasındaki iletişimi kolaylaştırmak için veya ile program arasında daha mantıklı olup olmadığına karar vermelisiniz. Aşağıdakilerden birini seçin:  
  
- Hata ayıklama oturumu ve DE arasındaki iletişimi kolaylaştırmak için daha mantıklı bir fikir varsa, hata ayıklama oturumu birlikte oluşturur ve bunu programa iliştirmesini ister. Bu, hata ayıklama oturumunu ve bir adres alanında birlikte, aynı zamanda çalışma zamanı ortamı ve program ile birlikte bir arada bırakır.  
  
- Ayrıca, ve programı arasındaki iletişimi kolaylaştırmak için daha anlamlı olursa çalışma zamanı ortamı da birlikte oluşturur. Bu, SDM 'yi bir adres alanında ve DE, çalışma zamanı ortamında ve programda birlikte bir arada bırakır. Bu, komut dosyalı dilleri çalıştırmak için bir yorumlayıcıyla uygulanan bir DE tipik bir davranıştır.  
  
    > [!NOTE]
    > Program ne iliştirir uygulamaya bağımlıdır. De ve program arasındaki iletişim uygulamaya bağımlıdır.  
  
## <a name="implementation"></a>Uygulama  
 Programlı olarak, oturum hata ayıklama Yöneticisi (SDM), başlatılacak programı temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) nesnesini ilk kez aldığında, [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) yöntemini çağırır ve daha sonra hata ayıklama olaylarını SDM 'ye geri geçirmek için kullanılan bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi iletir. `IDebugProgram2::Attach`Yöntemi daha sonra [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır. SDM 'nin arabirimi nasıl aldığı hakkında daha fazla bilgi için `IDebugProgram2` bkz. [bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md).  
  
 Ayrıca, hata ayıklamakta olan programla aynı adres alanında çalıştırılması gerekiyorsa, bu, genellikle bir betiği çalıştıran bir yorumlayıcının parçası olduğundan, `IDebugProgramNodeAttach2::OnAttach` yöntemi, `S_FALSE` Attach işlemini tamamladığını belirten olarak döner.  
  
 Öte yandan, diğer taraftan, SDM 'nin adres alanında da çalışıyorsa, `IDebugProgramNodeAttach2::OnAttach` yöntemi, `S_OK` [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi, hata ayıklanan programla ilişkili [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi üzerinde uygulanmaz. Bu durumda, [Attach yöntemi sonunda iliştirme işlemini](../../extensibility/debugger/reference/idebugengine2-attach.md) tamamlayacak şekilde çağırılır.  
  
 İkinci durumda, yöntemine geçirilen nesnede [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini çağırmanız `IDebugProgram2` `IDebugEngine2::Attach` , `GUID` Yerel program nesnesi içinde saklamanız ve `GUID` `IDebugProgram2::GetProgramId` yöntemi bu nesne üzerinde çağrıldığında bu işlemi geri döndürmelidir. , `GUID` Programı çeşitli hata ayıklama bileşenlerinde benzersiz bir şekilde tanımlamak için kullanılır.  
  
 `IDebugProgramNodeAttach2::OnAttach`Döndürülen yöntemin, `S_FALSE` `GUID` program için kullanım için bu yönteme geçtiğini ve `IDebugProgramNodeAttach2::OnAttach` `GUID` Yerel program nesnesinde ayarlayan yöntemi olduğunu unutmayın.  
  
 DE artık programa iliştirilir ve başlangıç olayları gönderilmeye hazırdır.  
  
## <a name="see-also"></a>Ayrıca Bkz.  
 [Doğrudan bir programa iliştirme](../../extensibility/debugger/attaching-directly-to-a-program.md)   
 [Bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md)   
 [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)   
 [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)   
 [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)   
 [Ekleme](../../extensibility/debugger/reference/idebugprogram2-attach.md)   
 [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)   
 [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)   
 [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)   
 [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)   
 [İliştir](../../extensibility/debugger/reference/idebugengine2-attach.md)

---
title: Bir başlatma Işleminden sonra iliştirme | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- debug engines, attaching to programs
ms.assetid: 5a3600a1-dc20-4e55-b2a4-809736a6ae65
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 3a4ce0a7465891035b43bbb8f6f22f0c064d104c
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "80739290"
---
# <a name="attach-after-a-launch"></a>Bir başlatma işleminden sonra Ekle
Bir program başlatıldıktan sonra, hata ayıklama oturumu, söz konusu programa hata ayıklama altyapısını (DE) eklemeye hazırdır.

## <a name="design-decisions"></a>Tasarım kararları
 İletişim, paylaşılan bir adres alanında daha kolay olduğundan, iki tasarım yaklaşımının arasından birini seçmeniz gerekir: hata ayıklama oturumu ile DE arasında iletişim ayarlayın. Ya da, ve programı arasındaki iletişimi ayarlayın. Aşağıdakilerden birini seçin:

- Hata ayıklama oturumu ve DE arasındaki iletişimi ayarlamayı daha anlamlı hale getirdiğinden hata ayıklama oturumu birlikte oluşturur ve bunu programa iliştirmesini ister. Bu tasarım, hata ayıklama oturumunu ve bir adres alanında birlikte, çalışma zamanı ortamı ile programı başka bir şekilde birlikte bırakır.

- Ayrıca, ve programı arasındaki iletişimi ayarlamayı daha mantıklı bir şekilde yapıyorsa, çalışma zamanı ortamı da birlikte oluşturur. Bu tasarım, SDM 'yi bir adres alanında ve DE, çalışma zamanı ortamında ve programda birlikte bir arada bırakır. Bu tasarım tipik olarak, betikleştirilmiş dilleri çalıştırmak için bir yorumlayıcıyla uygulanan bir DE vardır.

    > [!NOTE]
    > Program ne iliştirir uygulamaya bağımlıdır. De ve program arasındaki iletişim uygulamaya bağımlıdır.

## <a name="implementation"></a>Uygulama
 Programlı olarak, oturum hata ayıklama Yöneticisi (SDM), başlatılacak programı temsil eden [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md) nesnesini ilk kez aldığında, [Attach](../../extensibility/debugger/reference/idebugprogram2-attach.md) yöntemini çağırır ve daha sonra hata ayıklama olaylarını SDM 'ye geri geçirmek için kullanılan bir [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md) nesnesi iletir. `IDebugProgram2::Attach`Yöntemi daha sonra [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md) yöntemini çağırır. SDM 'nin arabirimi nasıl aldığı hakkında daha fazla bilgi için `IDebugProgram2` bkz. [bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md).

 Aynı adres alanında, hata ayıklaması yaptığınız programla aynı adres alanında çalışması gerekiyorsa, yöntemi, bir komut dosyası çalıştıran bir yorumlayıcının parçası olduğundan, `IDebugProgramNodeAttach2::OnAttach` yöntemi döndürür `S_FALSE` . `S_FALSE`Dönüş, iliştirme işlemini tamamladığını gösterir.

 Ancak,,, SDM 'nin adres alanında DE çalışır: `IDebugProgramNodeAttach2::OnAttach` Yöntem döner `S_OK` veya [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md) arabirimi, hata ayıkladığınız programla ilişkili [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) nesnesi üzerinde hiçbir şekilde uygulanmaz. Bu durumda, [Attach yöntemi sonunda iliştirme işlemini](../../extensibility/debugger/reference/idebugengine2-attach.md) tamamlayacak şekilde çağırılır.

 İkinci durumda, yöntemine geçirilen nesnede [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md) yöntemini çağırmanız `IDebugProgram2` `IDebugEngine2::Attach` , `GUID` Yerel program nesnesi içinde saklamanız ve `GUID` `IDebugProgram2::GetProgramId` yöntemi bu nesne üzerinde çağrıldığında bu işlemi geri döndürmelidir. , `GUID` Programı çeşitli hata ayıklama bileşenlerinde benzersiz bir şekilde tanımlamak için kullanılır.

 `IDebugProgramNodeAttach2::OnAttach`Döndürülen Yöntem durumunda, `S_FALSE` `GUID` program için kullanım için, bu yönteme geçirilir ve `IDebugProgramNodeAttach2::OnAttach` `GUID` Yerel program nesnesinde ayarlayan yöntemidir.

 DE artık programa iliştirilir ve başlangıç olayları gönderilmeye hazırdır.

## <a name="see-also"></a>Ayrıca bkz.
- [Doğrudan bir programa iliştirme](../../extensibility/debugger/attaching-directly-to-a-program.md)
- [Bağlantı noktasına bildirme](../../extensibility/debugger/notifying-the-port.md)
- [Hata ayıklama görevleri](../../extensibility/debugger/debugging-tasks.md)
- [IDebugEventCallback2](../../extensibility/debugger/reference/idebugeventcallback2.md)
- [IDebugProgram2](../../extensibility/debugger/reference/idebugprogram2.md)
- [İliştir](../../extensibility/debugger/reference/idebugprogram2-attach.md)
- [GetProgramId](../../extensibility/debugger/reference/idebugprogram2-getprogramid.md)
- [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md)
- [IDebugProgramNodeAttach2](../../extensibility/debugger/reference/idebugprogramnodeattach2.md)
- [OnAttach](../../extensibility/debugger/reference/idebugprogramnodeattach2-onattach.md)
- [İliştir](../../extensibility/debugger/reference/idebugengine2-attach.md)

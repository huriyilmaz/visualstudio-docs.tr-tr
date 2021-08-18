---
description: Aşağıdaki arabirimler, VS SDK kullanarak hata ayıklayıcıyı genişletmek için temel arabirimlerdir.
title: Çekirdek arabirimler | Microsoft Docs
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: leslierichardson95
ms.author: lerich
manager: jmartens
ms.technology: vs-ide-debug
ms.workload:
- vssdk
ms.openlocfilehash: 5dd69f5dd140118ea36ad02ff88bc36d6815616f
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122127655"
---
# <a name="core-interfaces"></a>Temel Arabirimler
Aşağıdaki arabirimler, kullanarak hata ayıklayıcıyı genişletmek için temel arabirimlerdir [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)] .

## <a name="discussion"></a>Tartışma
 Bu arabirimler öncelikle hata ayıklama altyapısını (DE) oluşturmak için kullanılır. Bunlar Kategoriler tarafından düzenlenmiştir:

- [Kesme noktaları](#Breakpoints)

- [Bağlamlar](#Contexts)

- [Çekirdek sunucu](#CoreServer)

- [Hata ayıklama motorları](#DebugEngines)

- [Belgeler](#Documents)

- [Ekinlikler](#Events)

- [İfadeler](#Expressions)

- [Bellek](#Memory)

- [Modül](#Modules)

- [Bağlantı noktaları](#Ports)

- [İşlemler](#Processes)

- [Programlar](#Programs)

- [Özellikler](#Properties)

- [Yığın Çerçeveleri](#StackFrames)

- [İş Parçacıkları](#Threads)

- [Tür Görselleştiriciler](#TypeVisualizers)

  Arabirimleri uygulayabilirler varlıkları şunlardır:

- Hata ayıklama altyapısı (DE)

- Bağlantı noktası sağlayıcısı (PS)

- İfade değerlendirici (EE)

- Visual Studio (vs)

## <a name="breakpoints"></a><a name="Breakpoints"></a> Kesme noktaları
 Bu arabirimler, kesme noktalarının uygulanmasıyla ve izlenleriyle ilgilidir.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Bir bellek konumuna dayalı bir kesme noktasını temsil eder.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Bir kesme noktası bir bellek konumuna bağlandığında DE tarafından gönderilir.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Kesme noktası isteği için bir belge sağlama toplamını temsil eder.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Bir kesme noktası bir bellek konumuna bağlanamazsa DE tarafından gönderilir.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Bir kesme noktasına ulaşıldığında DE tarafından gönderilir.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Kesme noktası için bir isteği temsil eder; bekleyen bir kesme noktası oluşturmak için kullanılır.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Kesme noktası için bir isteği temsil eder; bekleyen bir kesme noktası oluşturmak için kullanılır.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Bir kesme noktasını bağlamak için kullanılan bilgileri temsil eder.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Bir kesme noktasının bir bellek konumundan bağlantısı olmadığında DE tarafından gönderilir.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Geçersiz bir kesme noktasını (tarafından döndürülen `IDebugBreakpointErrorEvent2` ) temsil eder.|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Geçersiz bir kesme noktasıyla ilgili çözüm bilgilerini temsil eder.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Bir kesme noktasının ayarlandığı işlevdeki bir konumu temsil eder.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Bağlanacak bir kesme noktasını temsil eder; bağlantılı kesme noktası oluşturmak için kullanılır.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Bir bağlantılı kesme noktaları kümesi üzerinde bir numaralandırmayı temsil eder.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Bir bellek konumuna bağlanmayan kesme noktaları kümesi üzerinde bir numaralandırmayı temsil eder.|

## <a name="contexts"></a><a name="Contexts"></a> Lerden
 Bu arabirimler, hata ayıklamakta olan programın içindeki çeşitli bağlamlarını temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Bir kod yönergesinin başlangıç konumunu temsil eder.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Modül ve işlem arabirimlerinin alınmasını sağlamak için [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimini genişletir.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Belgedeki bir konumu temsil eder.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Bir ifadenin değerlendirileceği bağlamı temsil eder.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Bir bayt koleksiyonunun belleğindeki başlangıç konumunu temsil eder.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Kesme noktası veya özel durum üzerinde bir yığın çerçevesi bağlamını temsil eder.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Kesme noktası veya özel durum üzerinde bir yığın çerçevesi bağlamını temsil eder.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Bir kod bağlamı kümesi üzerinde bir sabit listesini temsil eder.|

## <a name="core-server"></a><a name="CoreServer"></a> Çekirdek sunucu
 Bu arabirimler, bir programın hata ayıklamakta olduğu makineyi temsil eder. Bunlar tarafından uygulanır, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ancak hata ayıklama motorları tarafından ' de çağrılabilir.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Bağlantı noktalarına ve bağlantı noktası tedarikçilerine ve bilgisayar hakkındaki bilgilere erişim sağlar.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Uzaktan hata ayıklamayı destekleyen bir [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md) temsil eder.|

## <a name="debug-engines"></a><a name="DebugEngines"></a> Hata ayıklama motorları
 Bu arabirimler hata ayıklama altyapılarını ve bunlarla ilişkili olayları temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Özel bir hata ayıklama altyapısını temsil eder.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Sembolleri, Adatmycode ve özel durumları yüklemeyi destekleyen özel bir hata ayıklama altyapısını temsil eder.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Aynı hata ayıklama görevlerinin işlenmesi için hazırlandığını göstermek için DE her yeni örneği tarafından gönderilir.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Programları başlatmayı destekleyen özel bir hata ayıklama altyapısını temsil eder.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Birden çok hata ayıklama altyapısını işleyen bir program düğümünü temsil eder.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|SDM 'nin bir iş parçacığı, program veya yığın çerçevesinden hata ayıklama altyapısına arabirim elde etmek için bir yol sağlar.|

## <a name="documents"></a><a name="Documents"></a> Belgelerini
 Bu arabirimler belgeleri (kaynak dosyaları) ve bunlarla ilişkili öğelerini temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|Açılacak bir belge istemek için DE ile gönderilir.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Belgedeki ayrıştırılmış yönergelerin akışını temsil eder.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|, Bir ad ve sınıf KIMLIĞI (CLSID) belirterek DE tarafından sağlanan bir belgeyi temsil eder.|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Bir hata ayıklama belgesi için bir sağlama toplamı temsil eder ve bileşenler arasında sağlama toplamı geçişine izin vermez.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Bir belge bağlamını, belirli bir ifadeye ve kod bağlamına karşılık gelen bir belge içindeki konumu temsil eder.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Bir belge içinde genel bir konumu temsil eder.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Kaynak dosyadaki bir konumu karakter boşluğu olarak temsil eder.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Gerçek metni sağlayarak DE ( [IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)öğesinden türetilmiş) tarafından sağlanan bir metin belgesini temsil eder.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|Bellekte olan bir kaynak dosyada yapılan değişiklikleri belirtmek için DE ile gönderilir.|

## <a name="events"></a><a name="Events"></a> Olayları
 Bu arabirimler, DE ve oturum hata ayıklama Yöneticisi (SDM) arasında gönderilen tüm olayları temsil eder.

| Arabirim | Uygulayan | Açıklama |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | Açılacak bir belge istemek için DE ile gönderilir. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Hata ayıklama altyapısı (DE), sembol yüklemeleri sırasında durum çubuğu iletisini ayarlamak için bu arayüzü oturum hata ayıklama Yöneticisi 'ne (SDM) gönderir. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Programda bir kesme tamamlandığında, tarafından gönderilir. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Bir kesme noktası bağlandığında DE ile gönderilir. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Bir kesme noktası bağlanamazsa DE ile gönderilir. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Bir kesme noktasına ulaşıldığında DE tarafından gönderilir. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Bir kesme noktasının bağlantısı olmadığında DE ile gönderilir. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Belirli bir konumda durması gerekip gerekmediğini öğrenmek için DE ile gönderilir. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | Bellekte olan bir kaynak dosyada yapılan değişiklikleri belirtmek için DE ile gönderilir. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Aynı hata ayıklama görevlerinin işlenmesi için hazırlandığını göstermek için DE her yeni örneği tarafından gönderilir. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Hata ayıklamakta olan programın ilk yönergeyi yürütmeye hazırlandığını göstermek için DE tarafından gönderilir. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | Başkaları tarafından okunabilen hata iletileri sağlamak için bir hata döndürebilen diğer olay arabirimleri tarafından kullanılan bir arabirim. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Diğer tüm olay arabirimlerinin türetildiği temel arabirim. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | (Belirli bir olay arabirimini uygulayan nesneler olarak ifade edilen) SDM tarafından uygulanan bir arabirimi temsil eder. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Hata ayıklamakta olan programda bir özel durum oluştuğunda DE tarafından gönderilir. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Zaman uyumsuz ifade değerlendirmesi tamamlandığında DE ile gönderilir. |
| IDebugFindSymbolEvent2 | | Dışı. KULLANMAYıN. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Yakalanamayan bir özel durum için işlem sırasında DE gönderilir. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Bir programın yüklenmesi tamamlandığında DE tarafından gönderilir. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | , IDE 'nin Kullanıcı için bilgilendirici bir ileti görüntülemesi için DE tarafından gönderilir. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Bir modül yüklendiğinde veya kaldırıldığında, ile gönderilir. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Hata ayıklayıcı Kullanıcı arabirimine, başlatılan yürütülebilir dosya için simgelerin konumlandırılamadığından kullanıcıyı uyarmasını sağlar. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | IDE 'nin rastgele bir dize görüntülemesi için DE ile gönderilir. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Bağlantı noktası olaylarını herhangi bir dinleyiciye iletmek için bir bağlantı noktası tarafından gönderilir. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Bir işlem oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Bir işlem yok edildiğinde DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Bir program oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Bir program yok edildiğinde DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Bir hata ayıklama oturumunu sonlandırdığınızda, bir hata ayıklama altyapısının Kullanıcı arabiriminin varsayılan davranışını geçersiz kılmasını sağlar [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] . |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Bir programın adı değiştiğinde, hata ayıklama altyapısından (DE) oturum hata ayıklama Yöneticisi 'ne (SDM) gönderilir. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Yeni bir Özellik (arabirime göre temsil edilir) oluşturulduğunda DE tarafından gönderilir `IDebugProperty2` . |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Bir özellik yok edildiğinde DE tarafından gönderilir. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | Ya da bir işlev üzerinden atlama sırasında, dönüş değerinin doğru görüntülenebilmesi için gönderilir. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Hata ayıklama altyapısının ölçüm ayarlarını uzaktan okumasını sağlar. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Yönergesi, üzerinde bir adımla, üzerinde veya sonunda bir adım tamamlandığında gönderilir. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | Bir modül için sembolleri yükleme başarısını veya başarısızlığını göstermek için DE ile gönderilir. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Bir iş parçacığı oluşturulduğunda DE tarafından gönderilir. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Bir iş parçacığı yok edildiğinde DE tarafından gönderilir. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Bir iş parçacığı adını değiştirdiyse DE tarafından gönderilir. |

## <a name="expressions"></a><a name="Expressions"></a> İfadelerde
 Bu arabirimler belirli bir bağlamda değerlendirilecek ifadeleri temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Değerlendirilecek bir ifadeyi temsil eder. [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabiriminden elde edilir.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Bir ifadenin değerlendirildiği bağlamı temsil eder. [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabiriminden elde edilir.|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Zaman uyumsuz ifade değerlendirmesi tamamlandığında DE ile gönderilir.|

## <a name="memory"></a><a name="Memory"></a> Bellek
 Bu arabirimler, bellekteki bayt dizilerini temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Okunan veya üzerine yazılan bellekteki bir bayt dizisini temsil eder.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Bir bayt dizisinin belleğindeki bir konumu temsil eder.|

## <a name="modules"></a><a name="Modules"></a> Modüler
 Bu arabirimler bir çalıştırılabilir veya .DLL dosyasına karşılık gelen bir modülü temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Tek bir yürütülebilir dosyayı veya DLL 'yi temsil eder.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Sembolleri destekleyen bir [IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md) temsil eder.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Bir modül yüklendiğinde veya kaldırıldığında, ile gönderilir.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB dosyasında bulunan kaynak sunucu bilgisini temsil eder.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|Bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)tarafından bilinen bir dizi modül üzerinde bir numaralandırmayı temsil eder.|

## <a name="ports"></a><a name="Ports"></a> Adet
 Bu arabirimler bağlantı noktalarını ve bağlantı noktası tedarikçilerini temsil eder.

| Arabirim | Uygulayan | Açıklama |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Yerel bilgisayardaki varsayılan bağlantı noktasını temsil eder. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Kullanıcı arabirimine, güvenlik duvarının uzaktan hata ayıklamayı engellememesini istemek IÇIN DCOM kullanan bir hata ayıklama altyapısı sağlar. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Bir bağlantı noktasını temsil eder. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Bağlantı noktası olaylarını herhangi bir dinleyiciye iletmek için bir bağlantı noktası tarafından gönderilir. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | İşlem başlatabilir ve sonlandırabilen bir bağlantı noktasını temsil eder. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Bir bağlantı noktası ile programları kaydetmek ve kaydını silmek için kullanılır; bağlantı noktasının hata ayıklamakta olan programları izlemesini sağlar. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Bağlantı noktasını seçmek için özelleştirilmiş bir kullanıcı arabirimini temsil eder. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Yeni bir bağlantı noktasının oluşturulacağı veya bulunduğu bağlantı noktası için bir isteği temsil eder. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Bir bağlantı noktası tedarikçisine temsil eder. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Oluşturduğu bağlantı noktalarıyla ilgili bilgileri (diske kaydet) kalıcı hale getirebileceği bir bağlantı noktası tedarikçisine temsil eder. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Kullanıcı arabiriminin, **İşleme İliştir** Iletişim kutusunun **Aktarım bilgileri** bölümünde metin görüntülemesini sağlar. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Hedef bilgisayar hakkında bilgi sorgulamak için izin verir. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Bir bağlantı noktası kümesi üzerinde bir numaralandırmayı temsil eder. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Bir dizi bağlantı noktası tedarikçilerinin bir kümesini temsil eder. |

## <a name="processes"></a><a name="Processes"></a> Lerse
 Bu arabirimler, bir veya daha fazla program içeren tek bir yürütülebilir dosya süreçlerini temsil eder.

|Arabirim|Uygulayan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Bir bilgisayarda çalışan bir işlemi temsil eder.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Etkin olarak hata ayıklamayı destekleyen bir işlemi temsil eder [(IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde Step, Continue ve Execute yöntemlerini değiştirmek için kullanılır).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Bir işlem oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Bir işlem yok edilirken DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Hangi oturumun ekli olduğunu izlemesi gereken bir işlemi temsil eder.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Bir bağlantı noktası üzerinde işlem kümesi bir numaralama temsil eder.|

## <a name="programs"></a><a name="Programs"></a> Program
 Bu arabirimler programları, fiziksel yürütülebilir dosya veya modüle karşılık gelen mantıksal yürütme birimlerini temsil eder.

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Aynı anda hata ayıklaması yapılan diğer programlarla birlikte çalışması gereken [bir IDebugProgram2'yi](../../../extensibility/debugger/reference/idebugprogram2.md) temsil eder.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Mantıksal yürütme birimini temsil eder.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Bir program oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Bir program yok edilirken DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Birden çok hata ayıklama altyapısı tarafından işlanlan bir [IDebugProgramNode2'yi](../../../extensibility/debugger/reference/idebugprogramnode2.md) temsil eder.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Hangi oturumun ekli olduğunu izlayabilmesi gereken [bir IDebugProgram2'yi](../../../extensibility/debugger/reference/idebugprogram2.md) temsil eder.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Çalıştırı olduğu işlem hakkında bilgi getiremeyen bir [IDebugProgram2'yi](../../../extensibility/debugger/reference/idebugprogram2.md) temsil eder.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Hata ayıklaması yapılan bir programı temsil eder.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Bir program düğümüne, ilişkili programa ekleme girişiminin bildir bildir 1000000000000000000000000000000000000000000|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|SDM'nin DE tarafından denetlenen programlar hakkında de sorgulaması için bir yol sağlar.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DE'ler tarafından, programların hata ayıklandıklarını göstermek amacıyla SDM'ye kaydolmak için kullanılır.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|Arabirimleri iş parçacığı veya işlem sınırları arasında sıralandıran [bir IDebugProgramNode2'yi](../../../extensibility/debugger/reference/idebugprogramnode2.md) temsil eder.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Bir dizi program için bir numaralama temsil eder.|

## <a name="properties"></a><a name="Properties"></a> Özellikler
 Bu arabirimler, genellikle bir ifade değerlendirmesinin sonucu olan belirli bir bağlamla ilişkili bir değer olan özellikleri temsil ediyor.

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Değerini özel [bir şekilde görüntüleyemeyen bir IDebugProperty2'yi](../../../extensibility/debugger/reference/idebugproperty2.md) temsil eder.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Bir yığın çerçevesinin, belgenin veya ifade değerlendirmesinin sonucu olan bir değeri temsil eder.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Rastgele uzun [dizeleri destekleyen bir IDebugProperty2'yi](../../../extensibility/debugger/reference/idebugproperty2.md) temsil eder.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Yeni bir özellik [(IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimiyle temsil edilen) oluşturulduğunda DE tarafından gönderilir.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Bir özellik yok edilirken DE tarafından gönderilir.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Belirli bir yığın çerçevesinin dışında varolan bir özelliğin başvurularını temsil eder.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Değişkenleri, yazmacı, parametreleri [ve ifadeleri DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) bir dizi veri kümesi üzerinde bir numaralama temsil eder.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|Bir dizi farklı yapı üzerinde bir [DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) temsil eder.|

## <a name="stack-frames"></a><a name="StackFrames"></a> Yığın Çerçeveleri
 Bu arabirimler, bir kesme noktası veya özel durumun meydana geldiği bir bağlam olan yığın çerçevesini temsil ediyor.

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Bir kesme noktası veya özel durumun meydana geldiği bağlamı temsil eder.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Araya gelen [özel durumları işleyemeyen bir IDebugStackFrame2'yi](../../../extensibility/debugger/reference/idebugstackframe2.md) temsil eder.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Belirli bir yığın çerçevesine varmak [için kullanılan işlev çağrı](../../../extensibility/debugger/reference/code-path.md) dizisini belirten CODE_PATH yapıları kümesi üzerinde bir numaralama temsil eder.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Yığın çerçevelerini açıklayan [bir DIZI FRAMEINFO yapısı](../../../extensibility/debugger/reference/frameinfo.md) üzerinde bir numaralama temsil eder.|

## <a name="threads"></a><a name="Threads"></a> Iş parçacığı
 Bu arabirimler iş parçacıklarını ve ilişkili olaylarını temsil ediyor.

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Yürütme iş parçacığını temsil eder.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Bir iş parçacığı oluşturulduğunda DE tarafından gönderilir.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Bir iş parçacığı yok olduğunda DE tarafından gönderilir.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Bir iş parçacığının adı değiştiriken DE tarafından gönderilir.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Bir dizi iş parçacığı üzerinde bir numaralama temsil eder.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a> Tür Görselleştiricileri
 Bu arabirimler tür görselleştiriciler için destek sağlar. Bu arabirimler genellikle bir ifade değerlendiricisi tarafından uygulanır.

|Arabirim|Uygulama tarafından|Açıklama|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Tür görselleştiriciye sunulacak bayt dizisini temsil eder.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Bir tür görselleştiriciye geçirilen verilere erişim elde etmek için yöntemler sağlar.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|[IPropertyProxyEESide uygulamalarına erişim sağlayan bir özelliği](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Özel Hata Ayıklama Altyapısı Oluşturma](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

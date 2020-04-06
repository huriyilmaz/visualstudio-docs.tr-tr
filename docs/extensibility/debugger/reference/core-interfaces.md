---
title: Çekirdek Arayüzler | Microsoft Dokümanlar
ms.date: 11/04/2016
ms.topic: reference
helpviewer_keywords:
- debugging [Debugging SDK], core interfaces
ms.assetid: 666b9116-8550-4bdd-bc15-55fc57de87df
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8bf01ffceb122ad99d5ecca8fabfaa102a8fc505
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80737586"
---
# <a name="core-interfaces"></a>Temel Arabirimler
Aşağıdaki arabirimler, hata ayıklamayı kullanarak genişleten çekirdek [!INCLUDE[vsipsdk](../../../extensibility/includes/vsipsdk_md.md)]arabirimleridir.

## <a name="discussion"></a>Tartışma
 Bu arabirimler öncelikle hata ayıklama altyapısı (DE) oluşturmak için kullanılır. Burada kategorilere göre düzenlenirler:

- [Kesme Noktaları](#Breakpoints)

- [Bağlamlar](#Contexts)

- [Çekirdek Sunucu](#CoreServer)

- [Hata Ayıklama Motorları](#DebugEngines)

- [Belgeler](#Documents)

- [Olaylar](#Events)

- [İfadeler](#Expressions)

- [Bellek](#Memory)

- [Modüller](#Modules)

- [Bağlantı Noktaları](#Ports)

- [Süreç](#Processes)

- [Programlar](#Programs)

- [Özellikler](#Properties)

- [Yığın Çerçeveleri](#StackFrames)

- [İş Parçacıkları](#Threads)

- [Tip Görselleştiriciler](#TypeVisualizers)

  Arabirimleri uygulayabilen varlıklar şunlardır:

- Hata Ayıklama Motoru (DE)

- Liman Tedarikçisi (PS)

- İfade Değerlendirici (EE)

- Görsel Stüdyo (VS)

## <a name="breakpoints"></a><a name="Breakpoints"></a>Kesme nokta -ları
 Bu arabirimler, kesme noktalarının uygulanması ve izlenmesiyle ilgilidir.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugBoundBreakpoint2](../../../extensibility/debugger/reference/idebugboundbreakpoint2.md)|DE|Bellek konumuna bağlı bir kesme noktasını temsil eder.|
|[IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md)|DE|Bir kesme noktası bellek konumuna bağlı olduğunda DE tarafından gönderilir.|
|[IDebugBreakpointChecksumRequest2](../../../extensibility/debugger/reference/idebugbreakpointchecksumrequest2.md)|VS|Kesme noktası isteği için belge denetimini temsil eder.|
|[IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md)|DE|Bir kesme noktası bellek konumuna bağlı başarısız olduğunda DE tarafından gönderilir.|
|[IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md)|DE|Bir kesme noktasına ulaşıldığında DE tarafından gönderilir.|
|[IDebugBreakpointRequest2](../../../extensibility/debugger/reference/idebugbreakpointrequest2.md)|VS|Kesme noktası isteğini temsil eder; bekleyen bir kesme noktası oluştururken kullanılır.|
|[IDebugBreakpointRequest3](../../../extensibility/debugger/reference/idebugbreakpointrequest3.md)|VS|Kesme noktası isteğini temsil eder; bekleyen bir kesme noktası oluştururken kullanılır.|
|[IDebugBreakpointResolution2](../../../extensibility/debugger/reference/idebugbreakpointresolution2.md)|DE|Kesme noktasını bağlamak için kullanılan bilgileri temsil eder.|
|[IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md)|DE|Bir kesme noktası bellek konumundan bağlanmamış olduğunda DE tarafından gönderilir.|
|[IDebugErrorBreakpoint2](../../../extensibility/debugger/reference/idebugerrorbreakpoint2.md)|DE|Geçersiz bir kesme noktasını temsil `IDebugBreakpointErrorEvent2`eder (döndürülür).|
|[IDebugErrorBreakpointResolution2](../../../extensibility/debugger/reference/idebugerrorbreakpointresolution2.md)|DE|Geçersiz bir kesme noktası yla ilgili çözüm bilgilerini temsil eder.|
|[IDebugFunctionPosition2](../../../extensibility/debugger/reference/idebugfunctionposition2.md)|DE|Kesme noktasının ayarlandığı bir işlevdeki konumu temsil eder.|
|[IDebugPendingBreakpoint2](../../../extensibility/debugger/reference/idebugpendingbreakpoint2.md)|DE|Bağlanacak bir kesme noktasını temsil eder; bağlı bir kesme noktası oluştururken kullanılır.|
|[IEnumDebugBoundBreakpoints2](../../../extensibility/debugger/reference/ienumdebugboundbreakpoints2.md)|DE|Bir dizi bağlı kesme noktası üzerinde numaralandırmayı temsil eder.|
|[IEnumDebugErrorBreakpoints2](../../../extensibility/debugger/reference/ienumdebugerrorbreakpoints2.md)|DE|Bellek konumuna bağlanamayan bir kesme noktaları kümesi üzerinde numaralandırmayı temsil eder.|

## <a name="contexts"></a><a name="Contexts"></a>Bağlam
 Bu arabirimler, debugged olan program içinde bağlamları çeşitli temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md)|DE|Kod talimatının başlangıç konumunu temsil eder.|
|[IDebugCodeContext3](../../../extensibility/debugger/reference/idebugcodecontext3.md)|DE|Modül ve işlem arabirimlerinin alınmasını sağlamak için [IDebugCodeContext2](../../../extensibility/debugger/reference/idebugcodecontext2.md) arabirimini genişletir.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Belgedeki bir konumu temsil eder.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Bir ifadeyi değerlendirecek bağlamı temsil eder.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Bayt koleksiyonunun belleğindeki başlangıç konumunu temsil eder.|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Kesme noktasındaveya özel durum da yığın çerçevesi bağlamı temsil eder.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Kesme noktasındaveya özel durum da yığın çerçevesi bağlamı temsil eder.|
|[IEnumDebugCodeContexts2](../../../extensibility/debugger/reference/ienumdebugcodecontexts2.md)|DE|Bir dizi kod bağlamı üzerinde numaralandırmayı temsil eder.|

## <a name="core-server"></a><a name="CoreServer"></a>Çekirdek Sunucu
 Bu arabirimler, bir programın debugged olduğu makineyi temsil eder. Bunlar hata ayıklama motorları tarafından [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] uygulanır, ancak hata ayıklama motorları tarafından çağrılabilir.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)|VS|Limanlara ve liman tedarikçilerine erişimin yanı sıra bilgisayar hakkında bilgi sağlar.|
|[IDebugCoreServer3](../../../extensibility/debugger/reference/idebugcoreserver3.md)|VS|Uzaktan hata ayıklamadestekleyen bir [IDebugCoreServer2'yi](../../../extensibility/debugger/reference/idebugcoreserver2.md) temsil eder.|

## <a name="debug-engines"></a><a name="DebugEngines"></a>Hata Ayıklama Motorları
 Bu arabirimler hata ayıklama altyapılarını ve bunların ilişkili olaylarını temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugEngine2](../../../extensibility/debugger/reference/idebugengine2.md)|DE|Özel hata ayıklama altyapıyı temsil eder.|
|[IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)|DE|Sembollerin, JustMyCode'un ve özel durumların yüklendiğini destekleyen özel bir hata ayıklama altyapıyı temsil eder.|
|[IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md)|DE|Hata ayıklama görevlerini işlemeye hazır olduğunu belirtmek için DE'nin her yeni örneği tarafından gönderilir.|
|[IDebugEngineLaunch2](../../../extensibility/debugger/reference/idebugenginelaunch2.md)|DE|Başlatma programlarını destekleyen özel bir hata ayıklama altyapısını temsil eder.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Birden çok hata ayıklama motorlarını işleyen bir program düğümlerini temsil eder.|
|[IDebugQueryEngine2](../../../extensibility/debugger/reference/idebugqueryengine2.md)|DE|SDM'nin iş parçacığı, program veya yığın çerçevesinden hata ayıklama altyapısına bir arabirim edinmesi için bir yol sağlar.|

## <a name="documents"></a><a name="Documents"></a>Belge
 Bu arabirimler belgeleri (kaynak dosyaları) ve bunların ilişkili öğelerini temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md)|DE|De tarafından açılacak bir belge istemek için gönderildi.|
|[IDebugDisassemblyStream2](../../../extensibility/debugger/reference/idebugdisassemblystream2.md)|DE|Bir belgeden sökülen yönergelerin akışını temsil eder.|
|[IDebugDocument2](../../../extensibility/debugger/reference/idebugdocument2.md)|VS, DE|De tarafından sağlanan bir belgeyi temsil eder ve bir ad ve sınıf kimliği (CLSID) belirtir.|
|[IDebugDocumentChecksum2](../../../extensibility/debugger/reference/idebugdocumentchecksum2.md)|DE, EE|Hata ayıklama belgesi için bir denetim ummasını temsil eder ve denetimleri bileşenler arasında geçirmeyi sağlar.|
|[IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)|VS, DE|Belge bağlamına, belge içindeki bir konumu belirli bir deyim ve kod bağlamına karşılık gelen bir konumu temsil eder.|
|[IDebugDocumentPosition2](../../../extensibility/debugger/reference/idebugdocumentposition2.md)|VS, DE|Belge içindeki genel konumu temsil eder.|
|[IDebugDocumentPositionOffset2](../../../extensibility/debugger/reference/idebugdocumentpositionoffset2.md)|VS|Kaynak dosyadaki bir konumu karakter ofset olarak temsil eder.|
|[IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)|VS, DE|Gerçek metni sağlayan DE [(IDebugDocument2'den](../../../extensibility/debugger/reference/idebugdocument2.md)türetilmiş) tarafından sağlanan bir metin belgesini temsil eder.|
|[IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md)|DE|BELLEKte olan bir kaynak dosyasında yapılan değişiklikleri belirtmek için DE tarafından gönderilir.|

## <a name="events"></a><a name="Events"></a>Olay
 Bu arabirimler, DE ile oturum hata ayıklama yöneticisi (SDM) arasında gönderilen tüm olayları temsil eder.

| Arabirim | Tarafından uygulanan | Açıklama |
| - |----------------| - |
| [IDebugActivateDocumentEvent2](../../../extensibility/debugger/reference/idebugactivatedocumentevent2.md) | DE | De tarafından açılacak bir belge istemek için gönderildi. |
| [IDebugBeforeSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugbeforesymbolsearchevent2.md) | DE | Hata ayıklama altyapısı (DE), bu arabirimi, sembol yükleri sırasında durum çubuğu iletisini ayarlamak üzere oturum hata ayıklama yöneticisine (SDM) gönderir. |
| [IDebugBreakEvent2](../../../extensibility/debugger/reference/idebugbreakevent2.md) | DE | Programda bir mola tamamlandığında DE tarafından gönderilir. |
| [IDebugBreakpointBoundEvent2](../../../extensibility/debugger/reference/idebugbreakpointboundevent2.md) | DE | Bir kesme noktası bağlı olduğunda DE tarafından gönderilir. |
| [IDebugBreakpointErrorEvent2](../../../extensibility/debugger/reference/idebugbreakpointerrorevent2.md) | DE | Bir kesme noktası bağlanamadığında DE tarafından gönderilir. |
| [IDebugBreakpointEvent2](../../../extensibility/debugger/reference/idebugbreakpointevent2.md) | DE | Bir kesme noktasına ulaşıldığında DE tarafından gönderilir. |
| [IDebugBreakpointUnboundEvent2](../../../extensibility/debugger/reference/idebugbreakpointunboundevent2.md) | DE | Bir kesme noktası bağlanmadığında DE tarafından gönderilir. |
| [IDebugCanStopEvent2](../../../extensibility/debugger/reference/idebugcanstopevent2.md) | DE | Belirli bir yerde durup durmayacağını belirlemek için DE tarafından gönderildi. |
| [IDebugDocumentTextEvents2](../../../extensibility/debugger/reference/idebugdocumenttextevents2.md) | DE | BELLEKte olan bir kaynak dosyasında yapılan değişiklikleri belirtmek için DE tarafından gönderilir. |
| [IDebugEngineCreateEvent2](../../../extensibility/debugger/reference/idebugenginecreateevent2.md) | DE | Hata ayıklama görevlerini işlemeye hazır olduğunu belirtmek için DE'nin her yeni örneği tarafından gönderilir. |
| [IDebugEntryPointEvent2](../../../extensibility/debugger/reference/idebugentrypointevent2.md) | DE | Debugged olan programın ilk talimatı yürütmek için hazır olduğunu belirtmek için DE tarafından gönderildi. |
| [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md) | DE | İnsan tarafından okunabilir hata iletileri sağlamak için bir hata döndürebilecek diğer olay arabirimleri tarafından kullanılan bir arabirim. |
| [IDebugEvent2](../../../extensibility/debugger/reference/idebugevent2.md) | DE, PS | Diğer tüm olay arabirimlerinin türetildiği temel arabirim. |
| [IDebugEventCallback2](../../../extensibility/debugger/reference/idebugeventcallback2.md) | VS | SDM tarafından uygulanan ve olayların (belirli bir olay arabirimini uygulayan nesneler olarak ifade edilen) gönderildiği bir arabirimi temsil eder. |
| [IDebugExceptionEvent2](../../../extensibility/debugger/reference/idebugexceptionevent2.md) | DE | Debugged olan programda bir özel durum oluştuğunda DE tarafından gönderilir. |
| [IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md) | DE | Eşzamanlı ifade değerlendirmesi tamamlandığında DE tarafından gönderilir. |
| IDebugFindSymbolEvent2 | | Eski. KULLANMAYıN. |
| [IDebugInterceptExceptionCompleteEvent2](../../../extensibility/debugger/reference/idebuginterceptexceptioncompleteevent2.md) | DE | Yakalanan bir özel durum için işleme tamamlandığında DE tarafından gönderildi. |
| [IDebugLoadCompleteEvent2](../../../extensibility/debugger/reference/idebugloadcompleteevent2.md) | DE | Bir program yükleme tamamlandığında DE tarafından gönderilir. |
| [IDebugMessageEvent2](../../../extensibility/debugger/reference/idebugmessageevent2.md) | DE | De tarafından IDE'nin kullanıcıya bir bilgilendirme iletisi görüntülemesi için gönderilir. |
| [IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md) | DE | Modül yüklendiğinde veya boşaltıldığında DE tarafından gönderilir. |
| [IDebugNoSymbolsEvent2](../../../extensibility/debugger/reference/idebugnosymbolsevent2.md) | DE | Kullanıcıyı, [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] başlatılan yürütülebilir için sembollerin bulunamadığını uyarmak için hata ayıklama ui sinyalleri. |
| [IDebugOutputStringEvent2](../../../extensibility/debugger/reference/idebugoutputstringevent2.md) | DE | DE tarafından IDE'nin rasgele bir dize görüntülemesi için gönderildi. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | VS, DE | Bağlantı noktası olaylarını herhangi bir dinleyiciye iletmek için bir bağlantı noktası tarafından gönderilir. |
| [IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md) | DE, PS | Bir işlem oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md) | DE, PS | Bir işlem yok edildiğinde DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md) | DE, PS | Bir program oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md) | DE, PS | Bir program yok edildiğinde DE veya bağlantı noktası tarafından gönderilir. |
| [IDebugProgramDestroyEventFlags2](../../../extensibility/debugger/reference/idebugprogramdestroyeventflags2.md) | DE | Hata ayıklama oturumunu sonladiğinizde [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] ui varsayılan davranışını geçersiz kılmak için hata ayıklama altyapısı sağlar. |
| [IDebugProgramNameChangedEvent2](../../../extensibility/debugger/reference/idebugprogramnamechangedevent2.md) | DE | Bir programın adı değiştiğinde hata ayıklama altyapısından (DE) oturum hata ayıklama yöneticisine (SDM) gönderilir. |
| [IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md) | DE | Yeni bir özellik `IDebugProperty2` (arabirim tarafından temsil edilen) oluşturulduğunda DE tarafından gönderilir. |
| [IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md) | DE | Bir mülk yok edildiğinde DE tarafından gönderilir. |
| [IDebugReturnValueEvent2](../../../extensibility/debugger/reference/idebugreturnvalueevent2.md) | DE | İade değerinin doğru bir şekilde görüntülenebilmeleri için bir işlevin dışına veya üstünden çıkarken DE tarafından gönderilir. |
| [IDebugSettingsCallback2](../../../extensibility/debugger/reference/idebugsettingscallback2.md) | VS | Hata ayıklama motorlarının metrik ayarları uzaktan okumasını sağlar. |
| [IDebugStepCompleteEvent2](../../../extensibility/debugger/reference/idebugstepcompleteevent2.md) | DE | Bir yönergeye giriş, son veya dış bir adım tamamlandığında DE tarafından gönderilir. |
| [IDebugSymbolSearchEvent2](../../../extensibility/debugger/reference/idebugsymbolsearchevent2.md) | DE | De tarafından bir modül için yükleme sembollerinin başarısını veya başarısızlığını belirtmek için gönderilir. |
| [IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md) | DE | Bir iş parçacığı oluşturulduğunda DE tarafından gönderilir. |
| [IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md) | DE | Bir iş parçacığı yok edildiğinde DE tarafından gönderilir. |
| [IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md) | DE | Bir iş parçacığı adını değiştirdiğinde DE tarafından gönderilir. |

## <a name="expressions"></a><a name="Expressions"></a>Ifa -de
 Bu arabirimler, belirli bir bağlamda değerlendirilecek ifadeleri temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugExpression2](../../../extensibility/debugger/reference/idebugexpression2.md)|DE|Değerlendirilecek bir ifadeyi temsil eder. [IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md) arabiriminden elde edilir.|
|[IDebugExpressionContext2](../../../extensibility/debugger/reference/idebugexpressioncontext2.md)|DE|Bir ifadenin değerlendirildiği bağlamı temsil eder. [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) arabiriminden elde edilir.|
|[IDebugExpressionEvaluationCompleteEvent2](../../../extensibility/debugger/reference/idebugexpressionevaluationcompleteevent2.md)|DE|Eşzamanlı ifade değerlendirmesi tamamlandığında DE tarafından gönderilir.|

## <a name="memory"></a><a name="Memory"></a>Bellek
 Bu arabirimler bellekteki bayt dizilerini temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugMemoryBytes2](../../../extensibility/debugger/reference/idebugmemorybytes2.md)|DE|Bellekteki okunabilir veya yazılabilir bayt dizisini temsil eder.|
|[IDebugMemoryContext2](../../../extensibility/debugger/reference/idebugmemorycontext2.md)|DE|Bayt dizisinin belleğindeki bir konumu temsil eder.|

## <a name="modules"></a><a name="Modules"></a>Modül
 Bu arabirimler, yürütülebilir veya . DLL dosyası.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugModule2](../../../extensibility/debugger/reference/idebugmodule2.md)|DE|Tek bir çalıştırılabilir veya DLL temsil eder.|
|[IDebugModule3](../../../extensibility/debugger/reference/idebugmodule3.md)|DE|Sembolleri destekleyen bir [IDebugModule2'yi](../../../extensibility/debugger/reference/idebugmodule2.md) temsil eder.|
|[IDebugModuleLoadEvent2](../../../extensibility/debugger/reference/idebugmoduleloadevent2.md)|DE|Modül yüklendiğinde veya boşaltıldığında DE tarafından gönderilir.|
|[IDebugSourceServerModule](../../../extensibility/debugger/reference/idebugsourceservermodule.md)|DE|PDB dosyasında bulunan kaynak sunucu bilgilerini temsil eder.|
|[IEnumDebugModules2](../../../extensibility/debugger/reference/ienumdebugmodules2.md)|DE|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)tarafından bilinen bir modül kümesi üzerinde numaralandırmayı temsil eder.|

## <a name="ports"></a><a name="Ports"></a>Bağlantı nokta -ları
 Bu arabirimler limanları ve bağlantı noktası tedarikçilerini temsil eder.

| Arabirim | Tarafından uygulanan | Açıklama |
| - |----------------| - |
| [IDebugDefaultPort2](../../../extensibility/debugger/reference/idebugdefaultport2.md) | VS, PS | Yerel bilgisayardaki varsayılan bağlantı noktasını temsil eder. |
| [IDebugFirewallConfigurationCallback2](../../../extensibility/debugger/reference/idebugfirewallconfigurationcallback2.md) | VS | Güvenlik duvarının uzaktan hata ayıklamayı [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] engellemeyeceğinden emin olmak için UI'den sormak için DCOM kullanan bir hata ayıklama altyapısı sağlar. |
| [IDebugPort2](../../../extensibility/debugger/reference/idebugport2.md) | VS, PS | Bir bağlantı noktasını temsil eder. |
| [IDebugPortEvents2](../../../extensibility/debugger/reference/idebugportevents2.md) | PS | Bağlantı noktası olaylarını herhangi bir dinleyiciye iletmek için bir bağlantı noktası tarafından gönderilir. |
| [IDebugPortEx2](../../../extensibility/debugger/reference/idebugportex2.md) | PS | İşlemleri başlatıp sonlandırabilecek bir bağlantı noktasını temsil eder. |
| [IDebugPortNotify2](../../../extensibility/debugger/reference/idebugportnotify2.md) | PS | Programları bir bağlantı noktasıyla kaydetmek ve kayıt dışı etmek için kullanılır; bağlantı noktasının şu anda debugged olan programları izlemesini sağlar. |
| [IDebugPortPicker](../../../extensibility/debugger/reference/idebugportpicker.md) | PS | Bağlantı noktasını seçmek için özelleştirilmiş bir ara birimi temsil eder. |
| [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) | VS | Yeni bir bağlantı noktasıoluşturulacak veya bulunacağı bir bağlantı noktası isteğini temsil eder. |
| [IDebugPortSupplier2](../../../extensibility/debugger/reference/idebugportsupplier2.md) | PS | Liman tedarikçisini temsil eder. |
| [IDebugPortSupplier3](../../../extensibility/debugger/reference/idebugportsupplier3.md) | PS | Oluşturduğu bağlantı noktaları yla ilgili bilgileri devam ettirebilen (diske kaydedebilirsiniz) bağlantı noktaları tedarikçisini temsil eder. |
| [IDebugPortSupplierDescription2](../../../extensibility/debugger/reference/idebugportsupplierdescription2.md) | PS | Kullanıcı Aracı'nın [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] **İşleme Ekle** iletişim kutusunun **Aktarım Bilgileri** bölümündeki metni görüntülemesini sağlar. |
| [IDebugWindowsComputerPort2](../../../extensibility/debugger/reference/idebugwindowscomputerport2.md) | VS | Hedef bilgisayar hakkında bilgi için sorgulama sağlar. |
| [IEnumDebugPorts2](../../../extensibility/debugger/reference/ienumdebugports2.md) | VS, PS | Bir dizi bağlantı noktası üzerinde numaralandırmayı temsil eder. |
| [IEnumDebugPortSuppliers2](../../../extensibility/debugger/reference/ienumdebugportsuppliers2.md) | VS | Bir dizi liman tedarikçisi üzerinde numaralandırmayı temsil eder. |

## <a name="processes"></a><a name="Processes"></a>Süreç
 Bu arabirimler, bir veya daha fazla program içeren tek bir yürütülebilir işlem temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugProcess2](../../../extensibility/debugger/reference/idebugprocess2.md)|PS, DE|Bilgisayarda çalışan bir işlemi temsil eder.|
|[IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)|PS, DE|Hata ayıklamaişlemini etkin olarak destekleyen bir işlemi temsil eder [(IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) arabiriminde Adım, Devam ve Yürüt metotlar yerine kullanılır).|
|[IDebugProcessCreateEvent2](../../../extensibility/debugger/reference/idebugprocesscreateevent2.md)|DE, PS|Bir işlem oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProcessDestroyEvent2](../../../extensibility/debugger/reference/idebugprocessdestroyevent2.md)|DE, PS|Bir işlem yok edildiğinde DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProcessEx2](../../../extensibility/debugger/reference/idebugprocessex2.md)|PS|Hangi oturumun bağlı olduğunu izlemesi gereken bir işlemi temsil eder.|
|[IEnumDebugProcesses2](../../../extensibility/debugger/reference/ienumdebugprocesses2.md)|PS|Bağlantı noktasındaki bir işlem kümesinin numaralandırması temsil eder.|

## <a name="programs"></a><a name="Programs"></a>Program
 Bu arabirimler programları, mutlaka fiziksel bir çalıştırılabilir veya modüle karşılık gelmez yürütme mantıksal birimleri temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugEngineProgram2](../../../extensibility/debugger/reference/idebugengineprogram2.md)|DE|Aynı anda debugged diğer programlar ile birlikte çalışması gereken bir [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md) temsil eder.|
|[IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)|DE, PS|Mantıksal bir yürütme birimini temsil eder.|
|[IDebugProgramCreateEvent2](../../../extensibility/debugger/reference/idebugprogramcreateevent2.md)|DE, PS|Bir program oluşturulduğunda DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProgramDestroyEvent2](../../../extensibility/debugger/reference/idebugprogramdestroyevent2.md)|DE, PS|Bir program yok edildiğinde DE veya bağlantı noktası tarafından gönderilir.|
|[IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)|DE, PS|Birden çok hata ayıklama motoru tarafından işlenebilen bir [IDebugProgramNode2'yi](../../../extensibility/debugger/reference/idebugprogramnode2.md) temsil eder.|
|[IDebugProgramEx2](../../../extensibility/debugger/reference/idebugprogramex2.md)|PS|Hangi oturumun bağlı olduğunu izleyebilen bir [IDebugProgram2'yi](../../../extensibility/debugger/reference/idebugprogram2.md) temsil eder.|
|[IDebugProgramHost2](../../../extensibility/debugger/reference/idebugprogramhost2.md)|DE, PS|Çalışma süreci hakkında bilgi döndürebilen bir [IDebugProgram2'yi](../../../extensibility/debugger/reference/idebugprogram2.md) temsil eder.|
|[IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)|DE, PS|Debugged olabilir bir programı temsil eder.|
|[IDebugProgramNodeAttach2](../../../extensibility/debugger/reference/idebugprogramnodeattach2.md)|DE, PS|Bir program düğümünün ilişkili programa ekleme girişimi hakkında bilgilendirilmesini sağlar.|
|[IDebugProgramProvider2](../../../extensibility/debugger/reference/idebugprogramprovider2.md)|DE|SDM'nin, o DE tarafından denetlenen programlar hakkında bir DE sorgusu için bir yol sağlar.|
|[IDebugProgramPublisher2](../../../extensibility/debugger/reference/idebugprogrampublisher2.md)|VS|DEs tarafından sdm ile program kayıt için debugged olduğunu göstermek için kullanılır.|
|[IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)|DE, PS|İş parçacığı veya işlem sınırları arasında arabirimleri işlenebilen bir [IDebugProgramNode2'yi](../../../extensibility/debugger/reference/idebugprogramnode2.md) temsil eder.|
|[IEnumDebugPrograms2](../../../extensibility/debugger/reference/ienumdebugprograms2.md)|DE, PS|Bir dizi programın numaralandırması temsil eder.|

## <a name="properties"></a><a name="Properties"></a>Özellikler
 Bu arabirimler, genellikle bir ifade değerlendirmesinin sonucu olan belirli bir bağlamla ilişkili bir değer olan özellikleri temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)|EE|Değerini özel bir şekilde görüntüleyebilen bir [IDebugProperty2'yi](../../../extensibility/debugger/reference/idebugproperty2.md) temsil eder.|
|[IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)|DE|Yığın çerçevesinin, belgenin veya ifade değerlendirmesinin sonucunu temsil eder.|
|[IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)|DE|Rasgele uzun dizeleri destekleyen bir [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) temsil eder.|
|[IDebugPropertyCreateEvent2](../../../extensibility/debugger/reference/idebugpropertycreateevent2.md)|DE|Yeni bir özellik [(IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md) arabirimi tarafından temsil edilen) oluşturulduğunda DE tarafından gönderilir.|
|[IDebugPropertyDestroyEvent2](../../../extensibility/debugger/reference/idebugpropertydestroyevent2.md)|DE|Bir mülk yok edildiğinde DE tarafından gönderilir.|
|[IDebugReference2](../../../extensibility/debugger/reference/idebugreference2.md)|DE|Belirli bir yığın çerçevesi dışında var olabilecek bir özelliğin başvurularını temsil eder.|
|[IEnumDebugPropertyInfo2](../../../extensibility/debugger/reference/ienumdebugpropertyinfo2.md)|DE|Değişkenleri, kayıtları, parametreleri ve ifadeleri açıklayan [bir dizi DEBUG_PROPERTY_INFO](../../../extensibility/debugger/reference/debug-property-info.md) yapıları üzerinde numaralandırmayı temsil eder.|
|[IEnumDebugReferenceInfo2](../../../extensibility/debugger/reference/ienumdebugreferenceinfo2.md)|DE|[DEBUG_REFERENCE_INFO](../../../extensibility/debugger/reference/debug-reference-info.md) yapıları kümesi üzerinde numaralandırmayı temsil eder.|

## <a name="stack-frames"></a><a name="StackFrames"></a>Yığın Çerçeveleri
 Bu arabirimler, kesme noktası veya özel durum oluştu bir bağlam, bir yığın çerçeve temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md)|DE|Kesme noktası veya özel durum oluştuğu bir bağlamı temsil eder.|
|[IDebugStackFrame3](../../../extensibility/debugger/reference/idebugstackframe3.md)|DE|Yakalanan özel durumları işleyebilir bir [IDebugStackFrame2](../../../extensibility/debugger/reference/idebugstackframe2.md) temsil eder.|
|[IEnumCodePaths2](../../../extensibility/debugger/reference/ienumcodepaths2.md)|DE|Belirli bir yığın çerçevesine ulaşmak için kullanılan işlev çağrı sırasını belirten [CODE_PATH](../../../extensibility/debugger/reference/code-path.md) yapıları kümesi üzerinde numaralandırmayı temsil eder.|
|[IEnumDebugFrameInfo2](../../../extensibility/debugger/reference/ienumdebugframeinfo2.md)|DE|Yığın çerçevelerini açıklayan [FRAMEINFO](../../../extensibility/debugger/reference/frameinfo.md) yapıları kümesi üzerinde numaralandırmayı temsil eder.|

## <a name="threads"></a><a name="Threads"></a>Iş parçacığı
 Bu arabirimler iş parçacıklarını ve ilişkili olayları temsil eder.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md)|DE|Yürütme iş parçacığı temsil eder.|
|[IDebugThreadCreateEvent2](../../../extensibility/debugger/reference/idebugthreadcreateevent2.md)|DE|Bir iş parçacığı oluşturulduğunda DE tarafından gönderilir.|
|[IDebugThreadDestroyEvent2](../../../extensibility/debugger/reference/idebugthreaddestroyevent2.md)|DE|Bir iş parçacığı yok edildiğinde DE tarafından gönderilir.|
|[IDebugThreadNameChangedEvent2](../../../extensibility/debugger/reference/idebugthreadnamechangedevent2.md)|DE|Bir iş parçacığı adını değiştirdiğinde DE tarafından gönderilir.|
|[IEnumDebugThreads2](../../../extensibility/debugger/reference/ienumdebugthreads2.md)|DE|Bir dizi iş parçacığı üzerinde numaralandırmayı temsil eder.|

## <a name="type-visualizers"></a><a name="TypeVisualizers"></a>Tip Görselleştiriciler
 Bu arabirimler, tür görüntüleyiciler için destek sağlar. Bu arabirimler genellikle bir ifade değerlendiricisi tarafından uygulanır.

|Arabirim|Tarafından uygulanan|Açıklama|
|---------------|--------------------|-----------------|
|[IEEDataStorage](../../../extensibility/debugger/reference/ieedatastorage.md)|EE|Bir tür görselleştiricisine sunulacak bir bayt dizisini temsil eder.|
|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md)|EE|Bir tür görselleştiricisine geçirilecek verilere erişim için yöntemler sağlar.|
|[IPropertyProxyProvider](../../../extensibility/debugger/reference/ipropertyproxyprovider.md)|EE|[IPropertyProxyEESide](../../../extensibility/debugger/reference/ipropertyproxyeeside.md) uygulamalarına erişim sağlayan bir özelliği temsil eder.|

## <a name="see-also"></a>Ayrıca bkz.
- [API Başvurusu](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)
- [Özel Hata Ayıklama Altyapısı Oluşturma](../../../extensibility/debugger/creating-a-custom-debug-engine.md)

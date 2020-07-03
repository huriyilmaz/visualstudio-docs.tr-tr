---
title: Etkin betik hata ayıklamasına genel bakış | Microsoft Docs
ms.custom: ''
ms.date: 01/18/2017
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Active Script Debugging overview
ms.assetid: ce4ec768-d017-4dfa-a7e3-cced3a29e679
caps.latest.revision: 11
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0181ee305c99a1d0af1d3e1e965c6ac8fe16f375
ms.sourcegitcommit: 9a9c61ca115c22d33bb902153eb0853789c7be4c
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/02/2020
ms.locfileid: "85835673"
---
# <a name="active-script-debugging-overview"></a>Etkin Komut Dosyası Hata Ayıklamaya Genel Bakış
Etkin betik hata ayıklama arabirimleri dilden bağımsız, ana bilgisayar bağımsız hata ayıklamasına izin verir ve çok çeşitli geliştirme ortamlarını destekler.  
  
 ![Betik ana bilgisayar Işlemi](../winscript/media/scp56activdbgarchgif.gif "Scp56ActivDbgArchgif")  
Şekil 1  
  
 Dilden bağımsız bir hata ayıklama ortamı, bu dillerden herhangi biriyle ilgili belirli bir bilgiye sahip olmadan, programlama dillerinin herhangi bir programlama dilini veya karışımını destekleyebilir. Hata ayıklama ortamı ayrıca diller arası adımlamayı ve kesme noktalarını destekler. (Bu genel bakış öncelikle VBScript ve gibi destek komut dosyası dillerinde odaklanır [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] .)  
  
 Ana bilgisayar bağımsız hata ayıklayıcı, Internet Explorer veya özel bir ana bilgisayar gibi herhangi bir etkin komut dosyası konağından otomatik olarak kullanılabilir. Konak, hata ayıklayıcının kullanıcıya ne sunduğunda, belge ağacının yapısından, hata ayıklama belgelerinin içerik ve sözdizimi renklendirmesinin ne olduğunu denetler. Bu, hata ayıklanan kaynak kodun konak belgesi bağlamında görünmesini sağlar. Örneğin, Internet Explorer bir HTML sayfasında betiği gösterebilir.  
  
 Aşağıdaki alt bölümlerde, etkin hata ayıklama içindeki her anahtar bileşen ve onunla ilişkili arabirimler ele alınmıştır. Ancak, daha sonra devam etmeden önce birkaç anahtar etkin hata ayıklama kavramı tanımlanmalıdır:  
  
 **Konak uygulaması**  
 Komut dosyası altyapılarını barındıran uygulama (veya "nesne modeli") komut dosyalı bir nesne kümesi sağlar.  
  
 **dil altyapısı**  
 Belirli bir dil için ayrıştırma, yürütme ve hata ayıklama soyutlamalarını sağlayan bir bileşen.  
  
 **hata ayıklayıcı IDE**  
 Konak uygulama ve dil altyapılarıyla iletişim kurarak hata ayıklama Kullanıcı arabirimi sağlayan uygulama.  
  
 **makine hata ayıklama Yöneticisi** Hata ayıklanabilir uygulama işlemlerinin kayıt defterini tutan bir bileşen.  
  
 **işlem hata ayıklama Yöneticisi**  
 Belirli bir uygulama için hata ayıklanabilir belgelerinin ağacını tutan, çalışan iş parçacıklarını izleyen ve bu şekilde devam eden bir bileşen.  
  
 **Belge bağlamı**  
 Belge bağlamı, bir konak belgesinin kaynak kodunda belirli bir aralığı temsil eden soyutlamadır.  
  
 **kod bağlamı**  
 Kod bağlamı, dil altyapısının çalışan kodundaki belirli bir konumu temsil eder ("sanal yönerge işaretçisi".)  
  
 **ifade bağlamı**  
 İfadelerin bir dil altyapısı tarafından değerlendirilebilecek belirli bir bağlam (örneğin, yığın çerçevesi).  
  
 **nesneye göz atma**  
 Bir "Gözcü penceresi" Kullanıcı arabirimini uygulamaya uygun bir nesnenin adının, türünün, değerinin ve alt nesnelerinin yapılandırılmış, dilden bağımsız bir gösterimi.  
  
 Aşağıda, her anahtar etkin hata ayıklama bileşeni ve ilgili, ilişkili arabirimler ve ardından bu arabirimlerin ayrıntıları yer aldığı bir genel bakış verilmiştir.  
  
## <a name="language-engine"></a>Dil altyapısı  
 Dil motoru şunları sağlar:  
  
- Dil ayrıştırma ve yürütme.  
  
- Hata ayıklama desteği (kesme noktaları vb.).  
  
- İfade değerlendirmesi.  
  
- Söz dizimi renklendirmesi.  
  
- Nesneye göz atma.  
  
- Yığın numaralandırması ve ayrıştırma.  
  
  Aşağıda, bir betik altyapısının hata ayıklama, ifade değerlendirmesi ve nesne taraması sağlamak için desteklemesi gereken arabirimler verilmiştir. Bu arabirimler, ana bilgisayar uygulaması tarafından belge bağlamı ve altyapının kod bağlamları arasında eşleme yapmak için ve ayrıca hata ayıklayıcı kullanıcı arabirimi tarafından ifade değerlendirmesi, yığın numaralandırması ve nesne taraması yapmak için kullanılır.  
  
  [IActiveScriptDebug Arabirimi](../winscript/reference/iactivescriptdebug-interface.md)  
  Sözdizimi renklendirme ve kod bağlamı numaralandırması sağlar.  
  
  [IActiveScriptErrorDebug Arabirimi](../winscript/reference/iactivescripterrordebug-interface.md)  
  Hatalar için belge bağlamlarını ve yığın çerçevelerini döndürür.  
  
  [IActiveScriptSiteDebug Arabirimi](../winscript/reference/iactivescriptsitedebug-interface.md)  
  Ana bilgisayar, komut dosyası altyapısından hata ayıklayıcıya bağlantı sağladı.  
  
  [IDebugCodeContext Arabirimi](../winscript/reference/idebugcodecontext-interface.md)  
  Bir iş parçacığında sanal bir "yönerge işaretçisi" sağlar.  
  
  [IEnumDebugCodeContexts Arabirimi](../winscript/reference/ienumdebugcodecontexts-interface.md)  
  Bir belge bağlamına karşılık gelen kod bağlamlarını numaralandırır.  
  
  [IDebugStackFrame Arabirimi](../winscript/reference/idebugstackframe-interface.md)  
  İş parçacığı yığınında bir mantıksal yığın çerçevesini temsil eder.  
  
  [IDebugExpressionContext Arabirimi](../winscript/reference/idebugexpressioncontext-interface.md)  
  , İfadelerin değerlendirileceği bağlamı sağlar.  
  
  [IDebugStackFrameSniffer Arabirimi](../winscript/reference/idebugstackframesniffer-interface.md)  
  Mantıksal yığın çerçevelerini numaralandırmak için bir yol sağlar.  
  
  [IDebugExpression Arabirimi](../winscript/reference/idebugexpression-interface.md)  
  Zaman uyumsuz olarak değerlendirilen bir ifadeyi temsil eder.  
  
  [IDebugSyncOperation Arabirimi](../winscript/reference/idebugsyncoperation-interface.md)  
  Bir betik altyapısının, belirli bir engellenen iş parçacığında iç içe yerleştirilmiş durumdayken gerçekleştirilmesi gereken bir işlemi soyutetmesine olanak tanır.  
  
  [IDebugAsyncOperation Arabirimi](../winscript/reference/idebugasyncoperation-interface.md)  
  Zaman uyumlu bir hata ayıklama işlemine zaman uyumsuz erişim sağlar.  
  
  [IDebugAsyncOperationCallBack Arabirimi](../winscript/reference/idebugasyncoperationcallback-interface.md)  
  Arabirim değerlendirmesinin ilerleme durumuyla ilgili durum olayları sağlar `IDebugAsyncOperation` .  
  
  [IEnumDebugExpressionContexts Arabirimi](../winscript/reference/ienumdebugexpressioncontexts-interface.md)  
  Bir nesne koleksiyonunu numaralandırır `IDebugExpressionContexts` .  
  
  [IProvideExpressionContexts Arabirimi](../winscript/reference/iprovideexpressioncontexts-interface.md)  
  Belirli bir bileşen tarafından bilinen ifade bağlamlarının numaralandırılması için bir yol sağlar.  
  
  [IDebugFormatter Arabirimi](../winscript/reference/idebugformatter-interface.md)  
  Bir dilin veya IDE 'nin DEĞIŞKEN değerler veya VARTYPE türleri ile dizeleri arasındaki dönüştürmeyi özelleştirmesini sağlar.  
  
  [IDebugStackFrameSnifferEx Arabirimi](../winscript/reference/idebugstackframesnifferex-interface.md)  
  PDM için mantıksal yığın çerçevelerini numaralandırır.  
  
## <a name="hosts"></a>Ana bilgisayarlar  
 Ana bilgisayar:  
  
- Dil altyapılarını barındırır.  
  
- Bir nesne modeli (komut dosyası olabilecek nesneler kümesi) sağlar.  
  
- Ayıklanabilecek belge ağacını ve bunların içeriğini tanımlar.  
  
- Betikleri sanal uygulamalar halinde düzenler.  
  
  İki tür ana bilgisayar vardır:  
  
- Dumb ana bilgisayarı yalnızca temel etkin komut dosyası arabirimlerini destekler. Belge yapısı veya kuruluşları üzerinde denetimi yoktur; Bu, tamamen dil altyapılarına sunulan betikler tarafından belirlenir.  
  
- Akıllı ana bilgisayar, belge ağacını, belge içeriğini ve söz dizimi renklendirmesini tanımlamaya olanak sağlayan daha büyük bir arabirim kümesini destekler. Bir ana bilgisayarın akıllı ana bilgisayar olmasını çok daha kolay hale getirmek için bir sonraki alt bölümde açıklanan yardımcı arabirimler kümesi vardır.  
  
### <a name="smart-host-helper-interfaces"></a>Akıllı ana bilgisayar yardımcı arabirimleri  
 `IDebugDocumentHelper`Yöntemler, bir konağın, tam konak arabirimlerinin tam karmaşıklığını (ve gücünden) işlemeksizin akıllı barındırma avantajlarından yararlanmak için kullanabileceği, büyük ölçüde basitleştirilmiş bir arabirim kümesi sağlar.  
  
 Bu arabirimlerin kullanılması için bir ana bilgisayar gerekli değildir. Ancak, bu arabirimlerin kullanılması, daha karmaşık birçok arabirimi uygulamaktan veya kullanmaktan kaçınabilirsiniz.  
  
 [IDebugDocumentHelper Arabirimi](../winscript/reference/idebugdocumenthelper-interface.md)  
 PDM tarafından uygulanır ve akıllı barındırma için gereken birçok arabirime yönelik uygulamalar sağlar.  
  
 [IDebugDocumentHost Arabirimi](../winscript/reference/idebugdocumenthost-interface.md)  
 Ana bilgisayar tarafından sözdizimi renklendirme gibi ana bilgisayara özgü işlevselliği göstermek için (isteğe bağlı olarak), hata ayıklayıcısına uygulanır.  
  
 Daha fazla bilgi için bkz. [akıllı konak yardımcı arabirimlerini uygulama](../winscript/implementing-smart-host-helper-interfaces.md).  
  
### <a name="full-smart-host-interfaces"></a>Tam akıllı konak arabirimleri  
 Aşağıda, bir akıllı ana bilgisayarın yardımcı arabirimleri kullanmıyor olması veya kullanması gereken arabirimlerin tam kümesi verilmiştir.  
  
 Ana bilgisayar tarafından uygulanan arabirimler:  
  
 [IDebugDocumentInfo Arabirimi](../winscript/reference/idebugdocumentinfo-interface.md)  
 Bir belge hakkında, örneği oluşturulmuş veya örneklenmemiş olabilecek bilgiler sağlar.  
  
 [IDebugDocumentProvider Arabirimi](../winscript/reference/idebugdocumentprovider-interface.md)  
 İsteğe bağlı bir belge örneği oluşturma araçlarını sağlar.  
  
 [IDebugDocument Arabirimi](../winscript/reference/idebugdocument-interface.md)  
 Tüm hata ayıklama belgelerinin temel arabirimi.  
  
 [IDebugDocumentText Arabirimi](../winscript/reference/idebugdocumenttext-interface.md)  
 Hata ayıklama belgesinin salt metin bir sürümüne erişim sağlar.  
  
 [IDebugDocumentTextAuthor Arabirimi](../winscript/reference/idebugdocumenttextauthor-interface.md)  
 Hata ayıklama belgesinin salt metin sürümünün düzenlenmesine izin verir.  
  
 [IDebugDocumentContext Arabirimi](../winscript/reference/idebugdocumentcontext-interface.md)  
 Hata ayıklamakta olan belgenin bir kısmının soyut gösterimini sağlar.  
  
 Konak adına PDM tarafından uygulanan arabirimler:  
  
 [IDebugApplicationNode Arabirimi](../winscript/reference/idebugapplicationnode-interface.md)  
 , `IDebugDocumentProvider` Bir proje ağacı içinde bir bağlam sağlayarak arabirimin işlevselliğini genişletir.  
  
## <a name="debugger-ide"></a>Hata ayıklayıcı IDE  
 IDE, dilden bağımsız bir hata ayıklama Kullanıcı arabirimi. Şu olanakları sunar:  
  
- Belge görüntüleyicileri/düzenleyiciler.  
  
- Kesme noktası yönetimi.  
  
- İfade değerlendirmesi ve gözcü pencereleri.  
  
- Yığın çerçevesine göz atma.  
  
- Nesne/sınıfa göz atma.  
  
- Sanal uygulama yapısına göz atma.  
  
  Hata ayıklayıcı tarafından uygulanan arabirimler:  
  
  [IApplicationDebugger Arabirimi](../winscript/reference/iapplicationdebugger-interface.md)  
  Bir hata ayıklayıcı IDE oturumu tarafından sunulan birincil arabirim.  
  
  [IApplicationDebuggerUI Arabirimi](../winscript/reference/iapplicationdebuggerui-interface.md)  
  Bir dış bileşene, hata ayıklayıcının Kullanıcı arabirimi (UI) üzerinde daha fazla denetim verir.  
  
  [IDebugExpressionCallBack Arabirimi](../winscript/reference/idebugexpressioncallback-interface.md)  
  Değerlendirme ilerlemesi için durum olayları sağlar `IDebugExpression` .  
  
  [IDebugDocumentTextEvents Arabirimi](../winscript/reference/idebugdocumenttextevents-interface.md)  
  İlişkili metin belgesinde yapılan değişiklikleri gösteren olayları sağlar.  
  
  [IDebugApplicationNodeEvents Arabirimi](../winscript/reference/idebugapplicationnodeevents-interface.md)  
  Arabirim için olay arabirimini sağlar `IDebugApplicationNode` .  
  
### <a name="machine-debug-manager"></a>Makine hata ayıklama Yöneticisi  
 Makine hata ayıklama Yöneticisi, etkin sanal uygulamaların bir listesini koruyup silerek sanal uygulamalar ve hata ayıklayıcılar arasında bağlama noktası sağlar.  
  
 [IDebugSessionProvider Arabirimi](../winscript/reference/idebugsessionprovider-interface.md)  
 Çalışan bir uygulama için hata ayıklama oturumu oluşturur.  
  
 [IMachineDebugManager Arabirimi](../winscript/reference/imachinedebugmanager-interface.md)  
 Makine hata ayıklama yöneticisinin birincil arabirimi.  
  
 [IMachineDebugManagerCookie Arabirimi](../winscript/reference/imachinedebugmanagercookie-interface.md)  
 `IMachineDebugManager`Arabirime benzer, ancak bu arabirim hata ayıklama tanımlama bilgilerini destekler.  
  
 [IMachineDebugManagerEvents Arabirimi](../winscript/reference/imachinedebugmanagerevents-interface.md)  
 Makine hata ayıklama Yöneticisi tarafından tutulan çalışan uygulama listesindeki değişikliklere işaret eder.  
  
 [IEnumRemoteDebugApplications Arabirimi](../winscript/reference/ienumremotedebugapplications-interface.md)  
 Bir makinedeki çalışan uygulamaları numaralandırır.  
  
### <a name="process-debug-manager"></a>İşlem Hata Ayıklama Yöneticisi  
 PDM şunları yapar:  
  
- Birden çok dil altyapısının hata ayıklamasını eşitler.  
  
- Hata ayıklanabilir belgelerinin ağacını tutar.  
  
- Yığın çerçevelerini birleştirir.  
  
- Kesme noktalarını ve dil altyapılarındaki adımlamayı koordine edin.  
  
- İş parçacıklarını izler.  
  
- Zaman uyumsuz işleme için bir hata ayıklayıcı iş parçacığı tutar.  
  
- Machine Debug Manager ve Debugger IDE ile iletişim kurar.  
  
  İşlem hata ayıklama Yöneticisi tarafından sunulan arabirimler aşağıda verilmiştir.  
  
  [IProcessDebugManager Arabirimi](../winscript/reference/iprocessdebugmanager-interface.md)  
  İşlem hata ayıklama yöneticisinin birincil arabirimi. Bu arabirim bir işlemden bir sanal uygulama oluşturabilir, ekleyebilir veya kaldırabilir.  
  
  [IRemoteDebugApplication Arabirimi](../winscript/reference/iremotedebugapplication-interface.md)  
  Çalışan bir uygulamayı temsil eder.  
  
  [IDebugApplication Arabirimi](../winscript/reference/idebugapplication-interface.md)  
  Dil motorları ve ana bilgisayarlar tarafından kullanılmak üzere uzaktan erişilebilir olmayan hata ayıklama yöntemlerini gösterir.  
  
  [IRemoteDebugApplicationThread Arabirimi](../winscript/reference/iremotedebugapplicationthread-interface.md)  
  Belirli bir uygulama içindeki yürütmenin iş parçacığını temsil eder.  
  
  [IDebugApplicationThread Arabirimi](../winscript/reference/idebugapplicationthread-interface.md)  
  Dil altyapılarının ve konakların iş parçacığı eşitlemesi sağlamasına ve iş parçacığına özgü, hata ayıklama durum bilgilerinin korunmasını sağlar.  
  
  [IEnumRemoteDebugApplicationThreads Arabirimi](../winscript/reference/ienumremotedebugapplicationthreads-interface.md)  
  Bir uygulamadaki çalışan iş parçacıklarını numaralandırır.  
  
  [IDebugThreadCall Arabirimi](../winscript/reference/idebugthreadcall-interface.md)  
  Sıralanmış çağrılar gönderir.  
  
  [IDebugApplicationNode Arabirimi](../winscript/reference/idebugapplicationnode-interface.md)  
  Hiyerarşideki bir belge için bir konum tutar.  
  
  [IEnumDebugApplicationNodes Arabirimi](../winscript/reference/ienumdebugapplicationnodes-interface.md)  
  Bir uygulamayla ilişkili bir düğümün alt düğümlerini numaralandırır.  
  
  [IEnumDebugStackFrames Arabirimi](../winscript/reference/ienumdebugstackframes-interface.md)  
  Altyapılardan birleştirilmiş bir iş parçacığına karşılık gelen yığın çerçevelerini numaralandırır.  
  
  [IDebugCookie Arabirimi](../winscript/reference/idebugcookie-interface.md)  
  Hata ayıklama tanımlama bilgisinin betik hata ayıklayıcılarına ayarlanmasına izin verir.  
  
  [IDebugHelper Arabirimi](../winscript/reference/idebughelper-interface.md)  
  , Nesne tarayıcıları için bir fabrika ve betik altyapısı için basit bağlantı noktaları işlevi görür.  
  
  [ISimpleConnectionPoint Arabirimi](../winscript/reference/isimpleconnectionpoint-interface.md)  
  Belirli bir bağlantı noktasında başlatılan olayları açıklamak ve listelemek için, komut dosyası motorları için basit bir yol sağlar.  
  
## <a name="see-also"></a>Ayrıca bkz.  
 [Etkin Betik Hata Ayıklayıcı Arabirimleri](../winscript/reference/active-script-debugger-interfaces.md)

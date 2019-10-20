---
title: Eski Iş akışı etkinlikleri | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
helpviewer_keywords:
- workflows, activities
- activities
- workflow activities
ms.assetid: 4af7a06b-1e82-43c8-aec8-0dc5fb63d08a
caps.latest.revision: 8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f4f1110424aefc1771c0dc7600fb9996bff0e892
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72658948"
---
# <a name="legacy-workflow-activities"></a>Eski İş Akışı Etkinlikleri
[!INCLUDE[wf](../includes/wf-md.md)], denetim akışı, koşullar, olay işleme, durum yönetimi ve uygulama ve hizmetlerle iletişim kurma için işlevsellik sağlayan varsayılan etkinlik kümesini içerir. İş akışlarını tasarlarken, [!INCLUDE[wfd1](../includes/wfd1-md.md)] tarafından sunulan sistem tarafından sağlanmış etkinlikleri kullanabilir veya kendi özel etkinliklerinizi oluşturabilirsiniz.

 Aşağıdaki tabloda [!INCLUDE[wf2](../includes/wf2-md.md)] Framework hazır olmayan etkinlik kümesi listelenmektedir. Bu etkinliklerin hepsi olmasa da çoğu, [!INCLUDE[wfd2](../includes/wfd2-md.md)] **araç kutusundan** erişilebilen etkinlik tasarımcıları tarafından temsil edilir. Etkinlik oluşturmak için **araç kutusu** ' ndan tasarımcısını sürükleyin ve tasarım yüzeyine bırakın.

|Etkinlik|Açıklama|
|--------------|-----------------|
|[CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025)|Yerel bir hizmetle giriş ve çıkış iletişimleri için **Handleexternaliventactivity** etkinliğiyle birlikte kullanılır. [CallExternalMethodActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65060)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[CancellationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65050)|Tüm bileşik etkinliğin alt öğelerinin yürütülmesi tamamlanmadan önce bileşik bir etkinliğin Temizleme mantığını içermesi için kullanılır. [CancellationHandlerActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65061)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[CodeActivity](http://go.microsoft.com/fwlink?LinkID=65026)|İş akışınıza Visual Basic veya C# kod eklemenize olanak sağlar. [CodeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65062)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[CompensatableSequenceActivity](http://go.microsoft.com/fwlink?LinkID=65027)|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)'nin Dengeleme sürümü. [CompensatableSequenceActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65002)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[CompensatableTransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65051)|**TransactionScopeActivity**'in telafi tablosu sürümü. [CompensatableTransactionScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65063)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[CompensateActivity](http://go.microsoft.com/fwlink?LinkID=65052)|Bir hata oluştuğunda iş akışı tarafından zaten gerçekleştirilen işlemleri dengelemek veya geri almak için kodu çağırmanızı sağlar. [telafi Teactivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65064)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[CompensationHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65053)|[CompensationHandlerActivity etkinliği kullanılarak](http://go.microsoft.com/fwlink?LinkID=65065)[!INCLUDE[crdefault](../includes/crdefault-md.md)] tamamlanmış bir TransactionScopeActivity etkinliği için tazminat gerçekleştiren bir veya daha fazla etkinlik için sarmalayıcı.|
|[ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017)|, [ConditionedActivityGroup](http://go.microsoft.com/fwlink?LinkID=65017) etkinliğinin kendisi için geçerli olan ve her bir alt öğeye ayrı uygulanan koşullara bağlı olarak alt etkinlikleri yürütür. [ConditionedActivityGroup etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65066)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[DelayActivity](http://go.microsoft.com/fwlink?LinkID=65028)|, Zaman aşımı aralığına göre iş akışınızda gecikme oluşturmanıza olanak sağlar. [DelayActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65067)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029)|Belirtilen bir olay gerçekleştiğinde yürütülen bir veya daha fazla etkinliği kaydırır. [EventDrivenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65068)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)|Etkinlikleri etkinliklerle ilişkilendirmek için bir çerçeve sağlar. [EventHandlersActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65069)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[EventHandlingScopeActivity](http://go.microsoft.com/fwlink?LinkID=65030)|Ana alt etkinliğini bir [EventHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65018)eşzamanlı olarak yürütür. [EventHandlingScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65070)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)|Belirttiğiniz bir türün özel durumunu işlemek için kullanılır. [FaultHandlerActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65071)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[FaultHandlersActivity](http://go.microsoft.com/fwlink?LinkID=65055)|[FaultHandlerActivity](http://go.microsoft.com/fwlink?LinkID=65054)türünde alt etkinliklerin sıralı listesine sahip olan bileşik bir etkinliği temsil eder. [FaultHandlersActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65072)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[Atanan](http://go.microsoft.com/fwlink?LinkID=65031)|Yerel bir hizmetle giriş ve çıkış iletişimleri için [CallExternalMethodActivity](http://go.microsoft.com/fwlink?LinkID=65025) etkinliğiyle birlikte kullanılır. [Handleexternaliventactivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65073)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)|Her dalda bir koşulu sınar ve koşulun **true**değerine eşit olduğu ilk dalda etkinlikleri gerçekleştirir. [IfElseActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65074)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[IfElseBranchActivity](http://go.microsoft.com/fwlink?LinkID=65034)|Bir [IfElseActivity](http://go.microsoft.com/fwlink?LinkID=65033)'nin dalını temsil eder. [IfElseBranchActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65075)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[InvokeWebServiceActivity](http://go.microsoft.com/fwlink?LinkID=65035)|Bir Web hizmetini çağırmak için iş akışınızı etkinleştirir. [InvokeWebServiceActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65076)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[InvokeWorkflowActivity](http://go.microsoft.com/fwlink?LinkID=65036)|İş akışınızın başka bir iş akışını çağırmasına olanak sağlar. [InvokeWorkflowActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65077)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[ListenActivity](http://go.microsoft.com/fwlink?LinkID=65037)|Yalnızca [EventDrivenActivity](http://go.microsoft.com/fwlink?LinkID=65029) alt etkinliklerini içeren bir bileşik etkinlik. [ListenActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65078)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[ParallelActivity](http://go.microsoft.com/fwlink?LinkID=65038)|Aynı anda işlenmek üzere iki veya daha fazla alt **SequenceActivity** etkinlik dalı zamanlamak için bir yol sağlar. [ParallelActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65079)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[PolicyActivity](http://go.microsoft.com/fwlink?LinkID=65019)|Kuralların koleksiyonunu temsil etmek için kullanın. Bir kural koşullardan ve sonuçta ortaya çıkan eylemlerden oluşur. [PolicyActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65004)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[ReplicatorActivity](http://go.microsoft.com/fwlink?LinkID=65039)|Tek bir alt etkinliğin birden fazla örneğini oluşturur. [ReplicatorActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65080)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[SequenceActivity](http://go.microsoft.com/fwlink?LinkID=65020)|Sıralı yürütme için birden çok etkinliği birbirine bağlamak için basit bir yol sağlar. [SequenceActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65081)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[SetStateActivity](http://go.microsoft.com/fwlink?LinkID=65041)|Yeni bir duruma geçiş belirtir. [SetStateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65082)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[StateActivity](http://go.microsoft.com/fwlink?LinkID=65042)|Durum makinesi iş akışındaki bir durumu temsil eder. [StateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65083)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[StateFinalizationActivity](http://go.microsoft.com/fwlink?LinkID=65043)|StateActivity **etkinliğinden** çıkılırken yürütülen alt etkinlikler için bir kapsayıcı olarak [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) etkinliğinde kullanılır. [StateFinalizationActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65008)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[StateInitializationActivity](http://go.microsoft.com/fwlink?LinkID=65044)|**StateActivity** etkinliği girilirken yürütülen alt etkinlikler için bir kapsayıcı olarak [StateActivity](http://go.microsoft.com/fwlink?LinkID=65042) etkinliğinde kullanılır. [StateInitializationActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65006)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[SuspendActivity](http://go.microsoft.com/fwlink?LinkID=65056)|Özel dikkat gerektiren bazı hata koşullarınız durumunda müdahalesini etkinleştirmek için iş akışınızın işlemini askıya alır. [SuspendActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65084)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[SynchronizationScopeActivity](http://go.microsoft.com/fwlink?LinkID=65057)|İçerilen etkinlikleri eşitlenmiş bir etki alanında sırayla yürütür. [SynchronizationScopeActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65085)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[TerminateActivity](http://go.microsoft.com/fwlink?LinkID=65058)|Bir hata koşulu durumunda iş akışınızın işlemini hemen sonlandırmanızı sağlar. [TerminateActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65086)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[ThrowActivity](http://go.microsoft.com/fwlink?LinkID=65059)|Bir iş akışı için işlem meta verilerinin bir parçası olarak oluşturulan iş özel durumlarını yakalamanızı sağlar. [ThrowActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65087)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[TransactionScopeActivity](http://go.microsoft.com/fwlink?LinkID=65093)|İşlemler ve özel durum işleme için bir çerçeve sağlar. Daha fazla bilgi için bkz. [TransactionScopeActivity etkinliğini kullanma](http://go.microsoft.com/fwlink?LinkID=65088).|
|[WebServiceFaultActivity](http://go.microsoft.com/fwlink?LinkID=65046)|Bir Web hizmeti hatasının oluşumunu modellemenize olanak sağlar. [WebServiceFaultActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65089)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[WebServiceInputActivity](http://go.microsoft.com/fwlink?LinkID=65047)|Bir Web hizmetinden veri alır. [WebServiceInputActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65090)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[Yanıt](http://go.microsoft.com/fwlink?LinkID=65048)|Bir iş akışına yapılan bir Web hizmeti isteğine yanıt verir. [WebServiceOutputActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65092)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|
|[WhileActivity](http://go.microsoft.com/fwlink?LinkID=65049)|Bir koşul karşılanana kadar iş akışınızın döngüye girmesine olanak sağlar. [WhileActivity etkinliğini kullanarak](http://go.microsoft.com/fwlink?LinkID=65091)[!INCLUDE[crdefault](../includes/crdefault-md.md)].|

 özel etkinlikler oluşturmayı [!INCLUDE[crabout](../includes/crabout-md.md)], bkz. [özel etkinlikler geliştirme](http://go.microsoft.com/fwlink?LinkID=65023) ve [eski etkinlik tasarımcısını kullanma](../workflow-designer/using-the-legacy-activity-designer.md).

## <a name="in-this-section"></a>Bu Bölümde
 [Etkinlik görünümleri (eski)](../workflow-designer/activity-views-legacy.md) Etkinliklerin farklı tasarım görünümlerini açıklar.

 [Nasıl yapılır: araç kutusuna etkinlik ekleme (eski)](../workflow-designer/how-to-add-activities-to-the-toolbox-legacy.md) Araç kutusuna etkinliklerin nasıl ekleneceğini gösterir.

 [Nasıl yapılır: bildirime dayalı bir kural koşulu oluşturma (eski)](../workflow-designer/how-to-create-a-declarative-rule-condition-legacy.md) Bildirim temelli bir kural koşulu oluşturma adımlarını gösterir.

 [Nasıl yapılır: PolicyActivity kural kümesi oluşturma (eski)](../workflow-designer/how-to-create-a-policyactivity-rule-set-legacy.md) Bir PolicyActivity kural kümesi oluşturma adımlarını gösterir.

 [Nasıl yapılır: WCF sözleşme Işlemi uygulama (eski)](../workflow-designer/how-to-implement-a-windows-communication-foundation-contract-operation-legacy.md) @No__t_1 bir sözleşme işlemi uygulamak için gereken adımları gösterir.

 [Nasıl yapılır: WCF sözleşme Işlemini çağırma (eski)](../workflow-designer/how-to-invoke-a-windows-communication-foundation-contract-operation-legacy.md) @No__t_1 sözleşmesi işlemini çağırma adımlarını gösterir.

## <a name="see-also"></a>Ayrıca Bkz.
 [Iş akışı etkinlikleri](http://go.microsoft.com/fwlink?LinkID=65023) geliştiren [iş akışları geliştiren](http://go.microsoft.com/fwlink?LinkID=65010) [Windows Workflow Foundation etkinlikleri](http://go.microsoft.com/fwlink?LinkID=65005)
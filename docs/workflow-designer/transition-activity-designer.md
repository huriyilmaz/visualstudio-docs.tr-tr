---
title: İş Akışı Tasarımcısı geçişi etkinlik Tasarımcısı
description: İki durum arasında geçiş yapılandırmak için geçiş etkinlik tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: cedc9c7b6f402ad3f5f2c40e21c29e2a0d1ad2e6
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433732"
---
# <a name="transition-activity-designer"></a>Transition Etkinlik Tasarımcısı

<xref:System.Activities.Statements.Transition>İki durum arasındaki geçişi temsil eder.

## <a name="using-the-transition-activity-designer"></a>Geçiş etkinliği tasarımcısını kullanma

Geçiş etkinliği Tasarımcısı iki durum arasında geçiş yapılandırmanızı sağlar.

### <a name="transition-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı geçiş özellikleri

Aşağıdaki tabloda, <xref:System.Activities.Statements.Transition> iş akışı Tasarımcısı kullanılarak ayarlanmakta olabilecek özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|Yanlış|Etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.Transition> . Varsayılan değer **T1** ' dir. Değer, genişletilmiş geçiş tasarımcısının üst bilgisinde ve genişletilmiş geçiş Tasarımcısı içindeki eylem bölümünde bulunan özellik kılavuzunda düzenlenebilir. , <xref:System.Activities.Activity.DisplayName%2A> İş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> <xref:System.Activities.Activity.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|Yanlış|Varsa, denetim hedef durumuna geçirilmeden önce **true** olarak değerlendirilmesi gereken bir ifade belirtir. Bu koşul, özellik kılavuzunda ve genişletilmiş geçiş tasarımcısında düzenlenebilir. Paylaşılan bir geçişte birden çok koşul, geçiş tasarımcısında göründükleri sırayla değerlendirilir. **Note:**  <xref:System.Activities.Statements.Transition.Condition%2A> Bir geçişin **yanlış** olarak değerlendirileceğini (veya paylaşılan bir tetikleyici geçişinin tüm koşullarını **false** olarak değerlendirdiğine), geçişin gerçekleşmeyeceğini ve durumdan gelen tüm geçişlerin her tetikleyicisinin yeniden planlanacağını unutmayın. Bu öğreticide, koşulların yapılandırıldığı şekilde bu durum gerçekleşmemelidir (tahminin doğru veya hatalı olması için özel eylemlerdir).|
|**Kaynak**|Doğru|Bu geçişin kaynaklandığı durumu gösterir. Kaynak durumunun adına tıklamak, tasarımcı görünümünü bu durumun genişletilmiş bir görünümüne geçirir. Bu değer, geçiş oluşturulduğunda ayarlanır ve değiştirilemez.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|Yanlış|Tamamlanması geçişi Başlatan etkinliği belirtir. Bu etkinliği ayarlamak için, **araç kutusundan** bir etkinliği sürükleyin ve geçişin **tetikleme** bölümüne bırakın.|
|<xref:System.Activities.Statements.Transition.Action%2A>|Yanlış|Tetikleyici etkinliği tamamlandığında ve varsa, <xref:System.Activities.Statements.Transition.Condition%2A> **doğru** sonucunu verirse yürütülen etkinliği belirtir. Bu etkinlik, <xref:System.Activities.Statements.State.Exit%2A> kaynak durumu için etkinlik varsa, hedef durumuna geçiş sırasında yürütülür. Geçiş Tasarımcısı genişletildiğinde, bu değer **araç kutusundan** bir etkinlik sürüklenerek geçişin **eylem** bölümüne bırakılarak ayarlanabilir. Tek bir geçiş için birden çok eylem olabilir. Tek tek eylemler genişletilebilir ve uygulanabilir olur ve bir geçişte birden çok eylem olduğunda, eylemde görüntülenen yukarı veya aşağı oka tıklanarak sıralanabilir.|
|**Hedef**|Doğru|Geçiş tamamlandıktan sonra durum makinesinin geçiş durumunu gösterir. Bu, <xref:System.Activities.Statements.Transition.To%2A> nesne modelindeki geçişin özelliğine karşılık gelir. Hedef durumunun adına tıklamak, tasarımcı görünümünü bu durumun genişletilmiş bir görünümüne geçirir. Bu değer, geçiş oluşturulduğunda ayarlanır ve geçişi tasarımcıda hedef durumuna bağlayan ok sürüklenerek değiştirilebilir.|

### <a name="creating-transitions"></a>Geçişler oluşturma

Geçişler bir durumdan diğerine sürüklenerek veya bir durum başka bir durum üzerinde sürüklendiğinde görüntülenen üçgenlere bir durum bırakılarak oluşturulur. Sürükleyerek bir geçiş oluşturmak için, fareyi kaynak durumunun kenarının üzerine getirin ve kaynak durumdan bir çizgiyi hedef durumuna sürükleyin. Bırakarak geçiş oluşturmak için, hedef durumunu sürükleyin ve kaynak durumunun üzerine gelin ve kaynak durumu etrafında görüntülenen dört üçgenden birine bırakın. Hedef durum, **araç kutusundan** sürüklenen yeni bir durum ya da iş akışı tasarımcısından sürüklenen mevcut bir durum olabilir.

> [!NOTE]
> Bir durum makinesindeki tek bir durum, iş akışı Tasarımcısı kullanılarak oluşturulan en fazla 76 geçişine sahip olabilir. Tasarımcı dışında oluşturulan iş akışları için bir durum geçişleri sınırı yalnızca sistem kaynaklarıyla sınırlıdır.

Paylaşılan tetikleyici geçişleri, aynı tetikleyici olayını paylaşan geçişler kümesidir. Paylaşılan tetikleyici, ortak bir tetikleyici olayını paylaşan birden çok geçiş için yapılandırılmış ifadelerin değerlendirmesine bağlı olarak bir hedef duruma yönelik koşullu ilerlemeyi sağlar. Bir geçişe ek eylemler eklemek ve paylaşılan bir geçiş oluşturmak için, istenen geçişin başlangıcını belirten daireye tıklayın ve istediğiniz duruma sürükleyin. Yeni geçiş, başlangıç geçişi olarak aynı tetikleyiciyi paylaşır, ancak benzersiz bir koşula ve eyleme sahip olur. Paylaşılan geçişler, geçiş Tasarımcısı ' nın altında **Paylaşılan tetikleyici geçişi ekle** ' ye tıklayarak geçiş Tasarımcısı içinden de oluşturulabilir ve sonra, bağlantı açılan listesinden, **kullanılabilir durumlar** ' da istenen hedef durumu seçebilirsiniz.

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Durum](../workflow-designer/state-activity-designer.md)

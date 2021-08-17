---
title: İş Akışı Tasarımcısı - Geçiş Etkinliği Tasarımcısı
description: İki eyalet arasında bir geçiş yapılandırmak için Geçiş etkinliği tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Transition.UI
ms.assetid: f6e8b5cc-7fb8-4699-9703-f3c9fc7cc316
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: a07642e195a3d589e32f2a78031e6d8749662299
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122025426"
---
# <a name="transition-activity-designer"></a>Transition Etkinlik Tasarımcısı

, <xref:System.Activities.Statements.Transition> iki durum arasındaki geçişi temsil eder.

## <a name="using-the-transition-activity-designer"></a>Geçiş Etkinlik Tasarımcısını Kullanma

Geçiş etkinliği tasarımcısı iki durum arasında bir geçiş yapılandırmaya olanak sağlar.

### <a name="transition-properties-in-the-workflow-designer"></a>Geçiş Özellikleri İş Akışı Tasarımcısı

Aşağıdaki tabloda iş <xref:System.Activities.Statements.Transition> akışı tasarımcısı kullanılarak ayarlanacak özellikler ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.Transition.DisplayName%2A>|Yanlış|Etkinlik tasarımcısının kolay <xref:System.Activities.Statements.Transition> adını belirtir. Varsayılan değer **T1'tir.** Değer, özellik kılavuzunda, genişletilmiş geçiş tasarımcısının üst bilgisinde ve genişletilmiş geçiş tasarımcısındaki eylem bölümünün üst bilgisinde düzenlenebilir. <xref:System.Activities.Activity.DisplayName%2A>, iş akışı tasarımcısının üst kısmında görüntülenen içerik harita gezintisinde kullanılır.<br /><br /> kesinlikle <xref:System.Activities.Activity.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.Transition.Condition%2A>|Yanlış|Varsa, denetim hedef durumuna geçirimeden önce **True** olarak değerlendirmesi gereken bir ifade belirtir. Bu koşul özellik kılavuzunda ve genişletilmiş geçiş tasarımcısında düzenlenebilir. Paylaşılan geçişte birden çok durum, geçiş tasarımcısında görünme sırasına göre değerlendirilir. **Not:**  Bir geçişin False (veya paylaşılan tetikleyici geçişinin tüm koşulları False olarak değerlendirilir) olarak değerlendirilirse, geçiş oluşmaz ve durumdan tüm geçişler için tüm tetikleyiciler yeniden <xref:System.Activities.Statements.Transition.Condition%2A> zamanlanmaz.   Bu öğreticide, koşulların yapılandırılması nedeniyle bu durum olamaz (tahminin doğru mu yoksa yanlış mı olduğuyla ilgili belirli eylemlerimiz vardır).|
|**Kaynak**|Doğru|Bu geçişin kaynaklandığı durumu gösterir. Kaynak durumunun adına tıklar, tasarımcı görünümünü bu durum için genişletilmiş bir görünüme iletir. Bu değer, geçiş oluşturulduğunda ayarlanır ve değiştirilemez.|
|<xref:System.Activities.Statements.Transition.Trigger%2A>|Yanlış|Tamamlanmasının geçişi başlattığı etkinliği belirtir. Bu etkinliği ayarlamak için Bir etkinliği Araç **Kutusundan sürükleyip** geçişin **Tetikleyici** bölümüne bırakın.|
|<xref:System.Activities.Statements.Transition.Action%2A>|Yanlış|Tetikleyici etkinliği tamamlandığında yürütülen etkinliği ve varsa , true olarak <xref:System.Activities.Statements.Transition.Condition%2A> değerlendirilir.  Bu etkinlik, varsa kaynak durumuna yönelik etkinlik yürütülürken hedef <xref:System.Activities.Statements.State.Exit%2A> durumuna geçişte yürütülür. Geçiş tasarımcısı genişletilirken, bu değer Araç Kutusundan  bir etkinliği sürükleyip geçişin **Eylem** bölümüne bırakarak ayarlanır. Tek bir geçiş için birden çok eylem olabilir. Tek tek eylemler genişletilebilir ve anlaşmalı olabilir ve bir geçişte birden çok eylem olduğunda eylemde görüntülenen yukarı veya aşağı oka tıklar.|
|**Hedef**|Doğru|Geçiş tamamlandıktan sonra durum makinesinin geçiş durumunu gösterir. Bu, nesne <xref:System.Activities.Statements.Transition.To%2A> modelinde geçişin özelliğine karşılık gelen bir özelliktir. Hedef durum adına tıklarken tasarımcı görünümü, bu durum için genişletilmiş bir görünüme geçiştir. Bu değer, geçiş oluşturulduğunda ayarlanır ve tasarımcıda geçişi hedef durumuna bağlayan ok sürüklenerek değiştirilebilir.|

### <a name="creating-transitions"></a>Geçiş oluşturma

Geçişler, bir çizginin bir durumdan diğerine sürüklenerek veya bir durum başka bir durum üzerine sürüklendikten sonra görünen üçgenlere bırakarak oluşturulur. Sürükleyerek geçiş oluşturmak için fareyi kaynak durumunun kenarının üzerine gelin ve bir satırı kaynak durumdan hedef durumuna sürükleyin. Bırakarak bir geçiş oluşturmak için hedef durumu sürükleyip kaynak durumunun üzerine gelin ve kaynak durumu çevresinde görünen dört üçgenden birinin üzerine bırakın. Hedef durum, Araç Kutusundan sürüklenen yeni bir durum **veya** iş akışı tasarımcısından sürüklenen mevcut bir durum olabilir.

> [!NOTE]
> Durum makinesinde tek bir durum, iş akışı tasarımcısı kullanılarak oluşturulan en fazla 76 geçişe sahip olabilir. Tasarımcı dışında oluşturulan iş akışları için durum geçişleri sınırı yalnızca sistem kaynaklarıyla sınırlıdır.

Paylaşılan tetikleyici geçişleri, aynı tetikleyici olayı paylaşan geçiş kümesidir. Paylaşılan tetikleyici, ortak bir tetikleyici olayı paylaşan birden çok geçiş için yapılandırılmış ifadelerin değerlendirilmesine dayalı olarak hedef durumuna koşullu ilerlemeye olanak sağlar. Bir geçişe ek eylemler eklemek ve paylaşılan bir geçiş oluşturmak için, istenen geçişin başlangıcını gösteren daireye tıklayın ve istenen durumuna sürükleyin. Yeni geçiş, ilk geçişle aynı tetikleyiciyi paylaşır, ancak benzersiz bir koşula ve eyleme sahip olur. Paylaşılan geçişler, geçiş tasarımcısının alt kısmından Paylaşılan tetikleyici geçişi ekle'ye tıklar ve ardından bağlanmak için Kullanılabilir durumlardan istenen hedef durum açılır listesinden seçerek geçiş tasarımcısının **içinde** oluşturulabilir. 

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Durum](../workflow-designer/state-activity-designer.md)

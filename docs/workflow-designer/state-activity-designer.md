---
title: İş Akışı Tasarımcısı - Durum Etkinliği Tasarımcısı
description: StateMachine etkinliği hakkında bilgi ve bir iş akışına durum eklemek için State etkinlik tasarımcısını nasıl kullanabileceğiniz hakkında bilgi edinmek.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 2a0d23bedea24a68285e90faf8ee39fd46de90fc
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963733"
---
# <a name="state-activity-designer"></a>State Etkinlik Tasarımcısı

, <xref:System.Activities.Statements.State> durum makinesinin içinde yer alan bir durumu temsil eder.

## <a name="using-the-state-activity-designer"></a>Durum Etkinliği Tasarımcısını Kullanma

Bir iş akışına eklemek için, Durum etkinliği tasarımcısını Araç Kutusunun State Machine bölümünden sürükleyin ve bu tasarımcının İş Akışı Tasarımcısı <xref:System.Activities.Statements.State>    <xref:System.Activities.Statements.StateMachine> bırakın. Bir etkinlik üzerine bırakılır ve daha sonra eklenen geçişler veya etkinlik <xref:System.Activities.Statements.State> <xref:System.Activities.Statements.StateMachine> bırakılırken <xref:System.Activities.Statements.State> bir geçiş oluşturulabilir. Bir etkinlik eklemek ve bir adımda geçiş oluşturmak için, Araç Kutusunun State Machine bölümünden bir State etkinliğini sürükleyin ve iş akışı tasarımcısında başka bir <xref:System.Activities.Statements.State> durum üzerine gelin.    Sürüklenen başka <xref:System.Activities.Statements.State> bir <xref:System.Activities.Statements.State> üzerine geldiğinde, diğerinde dört üçgen <xref:System.Activities.Statements.State> görünür. dört üçgenden biri üzerine bırakılırsa, durum makinesine eklenir ve kaynaktan bırakılan hedefe <xref:System.Activities.Statements.State> bir <xref:System.Activities.Statements.State> geçiş <xref:System.Activities.Statements.State> oluşturulur. Daha fazla bilgi için bkz. [Geçiş](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'da Durum Etkinliği Özellikleri

Aşağıdaki tabloda iş <xref:System.Activities.Statements.State> akışı tasarımcısı kullanılarak ayarlanacak özellikler ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özelliklerden bazıları özellik kılavuzunda, bazıları ise tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Yanlış|Üst bilgide etkinlik <xref:System.Activities.Statements.State> tasarımcısının kolay adını belirtir. Varsayılan değer State **değeridir.** Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. <xref:System.Activities.Statements.State.DisplayName%2A>, iş akışı tasarımcısının üst kısmında görüntülenen içerik harita gezintisinde kullanılır.<br /><br /> kesinlikle <xref:System.Activities.Statements.State.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.State.Entry%2A>|Yanlış|Bu durum'a geçiş olduğunda oluşan eylemi belirtir. Etkinlik genişletilirken, bu değer Araç Kutusundan bir etkinlik sürükleyerek ve durumun Giriş bölümüne <xref:System.Activities.Statements.State> **bırakarak**  ayarlanabilirsiniz.|
|<xref:System.Activities.Statements.State.Exit%2A>|Yanlış|Bu durum'dan geçiş olduğunda oluşan eylemi belirtir. Etkinlik <xref:System.Activities.Statements.State> genişletilirken, bir etkinlik Araç Kutusundan sürükleyip durumun **Çıkış** bölümüne bırakarak bu değer ayar olabilir. |
|<xref:System.Activities.Statements.State.Transitions%2A>|Yanlış|kaynağından kaynaklanan olası geçişleri <xref:System.Activities.Statements.State> listeler. Listede yer alan her öğenin ilişkili ve hedefine <xref:System.Activities.Statements.Transition> bir bağlantısı <xref:System.Activities.Statements.State> vardır. Bağlantıya tıklar, tasarımcıyı veya 'nin genişletilmiş görünümüne <xref:System.Activities.Statements.Transition> <xref:System.Activities.Statements.State> geçiştir.|

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)

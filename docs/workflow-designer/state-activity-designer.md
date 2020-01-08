---
title: İş Akışı Tasarımcısı durumu etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.State.UI
ms.assetid: 9455ab37-93a0-4c46-9eb8-b6611ca23167
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: f1a95808ec19edba01b266ccd280603bcc4321dc
ms.sourcegitcommit: d233ca00ad45e50cf62cca0d0b95dc69f0a87ad6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 01/01/2020
ms.locfileid: "75593154"
---
# <a name="state-activity-designer"></a>State Etkinlik Tasarımcısı

<xref:System.Activities.Statements.State>, bir durum makinesinin içinde olabilen bir durumu temsil eder.

## <a name="using-the-state-activity-designer"></a>Durum etkinliği tasarımcısını kullanma

Bir iş akışına bir <xref:System.Activities.Statements.State> eklemek için, **durum** etkinlik tasarımcısını **araç kutusunun** **durum makinesi** bölümünden sürükleyin ve iş akışı Tasarımcısı yüzeyinde bir <xref:System.Activities.Statements.StateMachine> etkinliğine bırakın. Bir <xref:System.Activities.Statements.State> etkinlik, daha sonra eklenen bir <xref:System.Activities.Statements.StateMachine> ve geçişlerin üzerine bırakılabilir; ya da <xref:System.Activities.Statements.State> etkinlik bırakılmadığı için bir geçiş oluşturulabilir. Bir <xref:System.Activities.Statements.State> etkinlik eklemek ve bir adımda geçiş oluşturmak için, **araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliği sürükleyin ve iş akışı tasarımcısında başka bir durum üzerine gelin. Sürüklenen <xref:System.Activities.Statements.State> başka bir <xref:System.Activities.Statements.State>üzerinde olduğunda, diğer <xref:System.Activities.Statements.State>etrafında dört üçgen görünür. <xref:System.Activities.Statements.State> dört üçgenden birine bırakıldığında, bu durum makineye eklenir ve kaynak <xref:System.Activities.Statements.State>, bırakılan hedef <xref:System.Activities.Statements.State>bir geçiş oluşturulur. Daha fazla bilgi için bkz. [geçiş](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı durum etkinliği özellikleri

Aşağıdaki tabloda, iş akışı Tasarımcısı kullanılarak ayarlayabilecekleri <xref:System.Activities.Statements.State> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özelliklerden bazıları özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Üst bilgide <xref:System.Activities.Statements.State> etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer **durumdur**. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. <xref:System.Activities.Statements.State.DisplayName%2A>, iş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A> kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Bu durum öğesine geçiş yapıldığında oluşan eylemi belirtir. <xref:System.Activities.Statements.State> etkinliği genişletildiğinde, bu değer **araç kutusundan** bir etkinlik sürüklenerek ve bu değeri durumun **giriş** bölümüne bırakarak ayarlanabilir.|
|<xref:System.Activities.Statements.State.Exit%2A>|False|Bu durum öğesinden uzağa geldiğinde oluşan eylemi belirtir. <xref:System.Activities.Statements.State> etkinliği genişletildiğinde, bu değer **araç kutusundan** bir etkinlik sürüklenerek durumun **Çıkış** bölümüne bırakılarak ayarlanabilir.|
|<xref:System.Activities.Statements.State.Transitions%2A>|False|<xref:System.Activities.Statements.State>kaynaklı olası geçişleri listeler. Listedeki her öğe, ilişkili <xref:System.Activities.Statements.Transition> ve hedef <xref:System.Activities.Statements.State>bağlantısını içerir. Bağlantıya tıkladığınızda tasarımcı <xref:System.Activities.Statements.Transition> veya <xref:System.Activities.Statements.State>genişletilmiş görünümüne geçiş yapılır.|

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)

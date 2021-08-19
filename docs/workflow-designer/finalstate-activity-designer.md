---
title: İş Akışı Tasarımcısı - FinalState Etkinlik Tasarımcısı
description: Bir durum makinesi örneğini sonlandıran bir State oluşturmak için FinalState tasarımcısını kullanmayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: a44cf8413e60b0dd5049f7ce31d699e6cfbbca47
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122099093"
---
# <a name="finalstate-activity-designer"></a>FinalState Etkinlik Tasarımcısı

Tasarımcı, <xref:System.Activities.Core.Presentation.FinalState> bir durum makinesi örneğini <xref:System.Activities.Statements.State> sonlandıran bir oluşturmak için kullanılır.

## <a name="using-the-finalstate-activity-designer"></a>FinalState Etkinlik Tasarımcısını Kullanma

**FinalState** tasarımcısı, bir durum makinesinde sonlandırıcı durum olarak <xref:System.Activities.Statements.State> önceden yapılandırılmış bir oluşturmak için kullanılır. Etkinlik tasarımcısı kullanılarak oluşturulan bir özelliği true olarak ayarlanmıştır, etkinliği yoktur ve bu <xref:System.Activities.Statements.State> <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State.IsFinal%2A>  <xref:System.Activities.Statements.State.Exit%2A> özellikten kaynaklanan hiçbir geçiş yoktur. Etkinlik tasarımcısını kullanarak bir durum makinesine sonlandırıcı durum olarak önceden yapılandırılmış bir etkinlik eklemek için, Araç Kutusunun State Machine bölümünden FinalState etkinlik tasarımcısını sürükleyin ve iş akışı tasarımcısına <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State> bırakın.    Etkinlik tasarımcısı bir ve geçişlerine daha sonra eklenebilir veya etkinlik tasarımcısı <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.StateMachine> bırakılırken <xref:System.Activities.Core.Presentation.FinalState> bir geçiş oluşturulabilir. Geçiş oluşturma hakkında daha fazla bilgi için bkz. [Geçiş.](../workflow-designer/transition-activity-designer.md)

### <a name="state-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı'da Durum Etkinliği Özellikleri

Aşağıdaki tabloda, tasarımcı kullanılarak ayarlanacak özellikler <xref:System.Activities.Core.Presentation.FinalState> ve bunların tasarımcıda nasıl kullanıldıkları açık bulunmaktadır. Bu özelliklerden bazıları özellik kılavuzunda, bazıları ise tasarımcı yüzeyinde düzenlenebilir.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Yanlış|Üst bilgide etkinlik <xref:System.Activities.Statements.State> tasarımcısının kolay adını belirtir. Varsayılan değer State **değeridir.** Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. <xref:System.Activities.Statements.State.DisplayName%2A>, iş akışı tasarımcısının üst kısmında görüntülenen içerik harita gezintisinde kullanılır.<br /><br /> kesinlikle <xref:System.Activities.Statements.State.DisplayName%2A> gerekli değildir, ancak bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.State.Entry%2A>|Yanlış|Bu durum'a geçiş olduğunda oluşan eylemi belirtir. Bu değer, Araç Kutusundan bir etkinliği **sürükleyip** durum bölümüne <xref:System.Activities.Statements.State.Entry%2A> bırakarak ayarlanır.|

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Durum](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
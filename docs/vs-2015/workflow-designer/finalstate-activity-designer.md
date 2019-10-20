---
title: Sonlandırdurum etkinlik Tasarımcısı | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
caps.latest.revision: 5
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: dff9793becc3e0619d42b642609273f328c6aa73
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72656720"
---
# <a name="finalstate-activity-designer"></a>FinalState Etkinlik Tasarımcısı
@No__t_0 Tasarımcısı, bir durum makine örneğini sonlandıran bir <xref:System.Activities.Statements.State> oluşturmak için kullanılır.

## <a name="using-the-finalstate-activity-designer"></a>FinalState etkinlik tasarımcısını kullanma
 **Sonlandırıcı durumu** Tasarımcısı, bir durum makinesinde sonlandırma durumu olarak önceden yapılandırılmış bir <xref:System.Activities.Statements.State> oluşturmak için kullanılır. @No__t_1 etkinlik Tasarımcısı kullanılarak oluşturulan <xref:System.Activities.Statements.State>, <xref:System.Activities.Statements.State.IsFinal%2A> özelliği **true**olarak ayarlanmıştır, <xref:System.Activities.Statements.State.Exit%2A> etkinliği yoktur ve bundan kaynaklı hiçbir geçiş yoktur. Bir durum makinesinde sonlandırma durumu olarak önceden yapılandırılmış bir <xref:System.Activities.Statements.State> etkinliği eklemek için <xref:System.Activities.Core.Presentation.FinalState> etkinlik tasarımcısını kullanmak için, **araç kutusu** 'Nun **durum makinesi** bölümünden **Sonlandırıcı durumu** etkinlik tasarımcısını sürükleyin ve iş akışı Tasarımcısı. @No__t_0 etkinlik Tasarımcısı, daha sonra eklenen bir <xref:System.Activities.Statements.StateMachine> ve geçişlerin üzerine bırakılabilir; ya da <xref:System.Activities.Core.Presentation.FinalState> etkinlik Tasarımcısı bırakılmadığı için bir geçiş oluşturulabilir. Geçiş oluşturma hakkında daha fazla bilgi için bkz. [geçiş](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı durum etkinliği özellikleri
 Aşağıdaki tabloda <xref:System.Activities.Core.Presentation.FinalState> Tasarımcısı kullanılarak ayarlanmakta olabilecek özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özelliklerden bazıları özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-------------------|--------------|-----------|
|<xref:System.Activities.Statements.State.DisplayName%2A>|False|Üst bilgide <xref:System.Activities.Statements.State> etkinlik tasarımcısının kolay adını belirtir. Varsayılan değer **durumdur**. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. @No__t_0, iş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> @No__t_0 kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.State.Entry%2A>|False|Bu durum öğesine geçiş yapıldığında oluşan eylemi belirtir. Bu değer, **araç kutusundan** bir etkinlik sürüklenerek ve bunu durumun <xref:System.Activities.Statements.State.Entry%2A> bölümüne bırakarak ayarlanabilir.|

## <a name="see-also"></a>Ayrıca Bkz.
 [StateMachine](../workflow-designer/statemachine-activity-designer.md) [durum](../workflow-designer/state-activity-designer.md) [geçişi](../workflow-designer/transition-activity-designer.md)
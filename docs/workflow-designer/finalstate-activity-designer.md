---
title: İş Akışı Tasarımcısı-FinalState etkinlik Tasarımcısı
description: Bir durum makine örneğini sonlandıran bir durum oluşturmak için FinalState tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: aa186893-8775-40dd-981f-8593ead831d0
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0a6ec51d17453a13f8c3ab1adffc5447afb5db7e
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99894185"
---
# <a name="finalstate-activity-designer"></a>FinalState Etkinlik Tasarımcısı

Tasarımcı, bir <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State> durum makine örneğini sonlandıran bir oluşturmak için kullanılır.

## <a name="using-the-finalstate-activity-designer"></a>FinalState etkinlik tasarımcısını kullanma

**Sonlandırıcı durumu** Tasarımcısı, <xref:System.Activities.Statements.State> bir durum makinesinde sonlandırma durumu olarak önceden yapılandırılmış bir oluşturmak için kullanılır. <xref:System.Activities.Statements.State>Etkinlik Tasarımcısı kullanılarak oluşturulan bir <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State.IsFinal%2A> , özelliği **true** olarak ayarlanmış, hiçbir etkinlik içermez <xref:System.Activities.Statements.State.Exit%2A> ve bundan kaynaklı hiçbir geçiş yoktur. <xref:System.Activities.Core.Presentation.FinalState> <xref:System.Activities.Statements.State> Bir durum makinesinde sonlandırma durumu olarak önceden yapılandırılmış bir etkinlik eklemek için etkinlik tasarımcısını kullanmak Için, **Sonlandırıcı durumu** etkinlik tasarımcısını **araç kutusunun** **durum makinesi** bölümünden sürükleyin ve iş akışı Tasarımcısı üzerine bırakın. <xref:System.Activities.Core.Presentation.FinalState>Etkinlik Tasarımcısı bir <xref:System.Activities.Statements.StateMachine> ve daha sonra eklenen geçişler üzerinde bırakılabilir veya <xref:System.Activities.Core.Presentation.FinalState> etkinlik Tasarımcısı bırakılmadığı için bir geçiş oluşturulabilir. Geçiş oluşturma hakkında daha fazla bilgi için bkz. [geçiş](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı durum etkinliği özellikleri

Aşağıdaki tabloda tasarımcı kullanılarak ayarlanmakta olabilecek özellikler gösterilmektedir <xref:System.Activities.Core.Presentation.FinalState> ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özelliklerden bazıları özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.State> . Varsayılan değer **durumdur**. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. , <xref:System.Activities.Statements.State.DisplayName%2A> İş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.State.Entry%2A>|Yanlış|Bu durum öğesine geçiş yapıldığında oluşan eylemi belirtir. Bu değer, **araç kutusundan** bir etkinlik sürüklenerek ve <xref:System.Activities.Statements.State.Entry%2A> durumunun bölümüne bırakılarak ayarlanabilir.|

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [Durum](../workflow-designer/state-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)
---
title: İş Akışı Tasarımcısı durumu etkinlik Tasarımcısı
description: Bir iş akışına durum eklemek için StateMachine etkinliği ve durum etkinliği tasarımcısını nasıl kullanabileceğinizi öğrenin.
ms.custom: SEO-VS-2020
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
ms.openlocfilehash: d5dbe0a14b007ad8e916aa9b2d8d765402dbe66b
ms.sourcegitcommit: ed26b6e313b766c4d92764c303954e2385c6693e
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 11/10/2020
ms.locfileid: "94433992"
---
# <a name="state-activity-designer"></a>State Etkinlik Tasarımcısı

Bir <xref:System.Activities.Statements.State> durum makinesinin içinde olabilecek bir durumu temsil eder.

## <a name="using-the-state-activity-designer"></a>Durum etkinliği tasarımcısını kullanma

Bir iş akışına bir eklemek için <xref:System.Activities.Statements.State> , **durum** etkinlik tasarımcısını **araç kutusunun** **durum makinesi** bölümünden sürükleyin ve <xref:System.Activities.Statements.StateMachine> iş akışı Tasarımcısı yüzeyinde bir etkinliğe bırakın. Bir <xref:System.Activities.Statements.State> etkinlik bir <xref:System.Activities.Statements.StateMachine> ve daha sonra eklenen geçişler üzerinde bırakılabilir veya <xref:System.Activities.Statements.State> etkinlik bırakılmakta olduğundan bir geçiş oluşturulabilir. <xref:System.Activities.Statements.State>Tek adımda bir etkinlik eklemek ve bir geçiş oluşturmak için, **araç kutusunun** **durum makinesi** bölümünden bir **durum** etkinliği sürükleyin ve iş akışı tasarımcısında başka bir durum üzerine gelin. Sürüklenen <xref:System.Activities.Statements.State> bir diğerinin üzerindeyken <xref:System.Activities.Statements.State> , diğerinin etrafında dört üçgen görünür <xref:System.Activities.Statements.State> . <xref:System.Activities.Statements.State>Dört üçgenden birine bırakıldığında, durum makinesine eklenir ve kaynaktan bırakılan hedefe bir geçiş oluşturulur <xref:System.Activities.Statements.State> <xref:System.Activities.Statements.State> . Daha fazla bilgi için bkz. [geçiş](../workflow-designer/transition-activity-designer.md).

### <a name="state-activity-properties-in-the-workflow-designer"></a>İş Akışı Tasarımcısı durum etkinliği özellikleri

Aşağıdaki tabloda, <xref:System.Activities.Statements.State> iş akışı Tasarımcısı kullanılarak ayarlanmakta olabilecek özellikler gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özelliklerden bazıları özellik kılavuzunda düzenlenebilir ve bazıları tasarımcı yüzeyinde düzenlenebilirler.

|Özellik Adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Statements.State.DisplayName%2A>|Yanlış|Başlıktaki etkinlik tasarımcısının kolay adını belirtir <xref:System.Activities.Statements.State> . Varsayılan değer **durumdur**. Değer, özellik kılavuzunda veya doğrudan etkinlik tasarımcısının üst bilgisinde düzenlenebilir. , <xref:System.Activities.Statements.State.DisplayName%2A> İş akışı tasarımcısının üst kısmında görüntülenen içerik haritası gezintisinde kullanılır.<br /><br /> <xref:System.Activities.Statements.State.DisplayName%2A>Kesinlikle gerekli olmasa da, bir tane kullanmak en iyi uygulamadır.|
|<xref:System.Activities.Statements.State.Entry%2A>|Yanlış|Bu durum öğesine geçiş yapıldığında oluşan eylemi belirtir. <xref:System.Activities.Statements.State>Etkinlik genişletildiğinde, bu değer **araç kutusundan** bir etkinlik sürüklenerek durumun **giriş** bölümüne bırakılarak ayarlanabilir.|
|<xref:System.Activities.Statements.State.Exit%2A>|Yanlış|Bu durum öğesinden uzağa geldiğinde oluşan eylemi belirtir. <xref:System.Activities.Statements.State>Etkinlik genişletildiğinde, bu değer **araç kutusundan** bir etkinlik sürüklenerek durumun **Çıkış** bölümüne bırakılarak ayarlanabilir.|
|<xref:System.Activities.Statements.State.Transitions%2A>|Yanlış|Kaynağından kaynaklanan olası geçişleri listeler <xref:System.Activities.Statements.State> . Listedeki her öğe, ilişkili ve hedefe bir bağlantı içerir <xref:System.Activities.Statements.Transition> <xref:System.Activities.Statements.State> . Bağlantıya tıkladığınızda tasarımcı veya uygulamasının genişletilmiş görünümüne geçiş yapılır <xref:System.Activities.Statements.Transition> <xref:System.Activities.Statements.State> .|

## <a name="see-also"></a>Ayrıca bkz.

- [StateMachine](../workflow-designer/statemachine-activity-designer.md)
- [FinalState](../workflow-designer/finalstate-activity-designer.md)
- [Transition](../workflow-designer/transition-activity-designer.md)

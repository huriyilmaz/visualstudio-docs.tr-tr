---
title: İş Akışı Tasarımcısı-kalıcı etkinlik Tasarımcısı
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- System.Activities.Statements.Persist.UI
ms.assetid: be8648dd-3eb9-4a50-8ec1-57a8be804692
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 882a68e006ac139d717320b0b8b7ce4d75aceb38
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72650113"
---
# <a name="persist-activity-designer"></a>Persist Etkinlik Tasarımcısı

**Kalıcı** etkinlik Tasarımcısı <xref:System.Activities.Statements.Persist> etkinlik oluşturmak ve yapılandırmak için kullanılır.

## <a name="the-persist-activity"></a>Kalıcı etkinlik

@No__t_0 etkinliği, mümkünse bir iş akışını diske kaydeder. @No__t_0 etkinliği, örneğin bir <xref:System.Activities.Statements.TransactionScope> etkinliği içinde, kalıcılık olmayan bir bölgede yürütülemez. Kalıcı olmayan bir kapsamda <xref:System.Activities.Statements.Persist> etkinliğini kullanıyorsanız, çalışma zamanında bir özel durum oluşturulur.

### <a name="using-the-persist-activity-designer"></a>Kalıcı etkinlik tasarımcısını kullanma

**Kalıcı** etkinlik **Tasarımcısı araç kutusu sekmesine** tıklanarak erişilen (alternatif olarak, **Görünüm** menüsünden **araç kutusu** ' nu veya Ctrl + Alt + X ' i seçerek **),** **çalışma alanının çalışma zamanı** kategorisinde bulunabilir.

**Kalıcı** etkinlik Tasarımcısı **araç kutusundan** sürüklenip, her durumda (örneğin, <xref:System.Activities.Statements.Sequence> gibi) iş akışı Tasarımcısı yüzeyine bırakılabilir. Bu, varsayılan olarak **görünmeyen** bir <xref:System.Activities.Statements.Persist> etkinliği oluşturur. @No__t_0, **kalıcı** etkinlik tasarımcısının üst bilgisinde veya özellik kılavuzunun **DisplayName** kutusunda düzenlenebilir.

### <a name="the-persist-properties"></a>Devam eden özellikler

Aşağıdaki tabloda <xref:System.Activities.Statements.Persist> özellikleri gösterilmektedir ve bunların tasarımcıda nasıl kullanıldığı açıklanmaktadır. Bu özellikler özellik kılavuzunda düzenlenebilir ve bazıları İş Akışı Tasarımcısı yüzeyinde düzenlenebilirler.

|Özellik adı|Gerekli|Kullanım|
|-|--------------|-|
|<xref:System.Activities.Activity.DisplayName%2A>|False|@No__t_0 etkinliğinin kolay adı. Varsayılan değer korunur. Görünen ad kesinlikle gerekli olmasa da, bir görünen ad kullanmak en iyi uygulamadır.|

## <a name="see-also"></a>Ayrıca bkz.

- [Çalışma Zamanı](../workflow-designer/runtime-activity-designers.md)
- [TerminateWorkflow](../workflow-designer/terminateworkflow-activity-designer.md)
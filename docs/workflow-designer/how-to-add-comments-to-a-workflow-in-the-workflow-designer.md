---
title: 'İş Akışı Tasarımcısı-nasıl yapılır: bir iş akışına açıklama ekleme'
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 77fb43671a45d5d53d2fe23fa3e4e7a9a98c4373
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85815506"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısında bir iş akışına açıklama ekleme

Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için .NET Framework 4,5, geliştiricinin tasarımcı içindeki aşağıdaki öğe türlerine ek açıklamalar eklemesine izin verir:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Türetilmiş sınıflar<xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Ek açıklamanın içerikleri, iş akışıyla ilişkili XAML dosyasına düz metin olarak kaydedilir ve başkaları tarafından okunabilir. Hassas bilgileri bir ek açıklamaya girerken dikkatli olun.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Tasarımcıda bir etkinliğe ek açıklama ekleme

1. İş akışı tasarımcısında, iş akışı tasarımcısında bir öğeye sağ tıklayın ve **ek** **Açıklama Ekle**' yi seçin.

1. Ek açıklamanın metnini, girilen alana ekleyin.

   Öğe bir ek açıklama simgesi gösterir. Ek açıklama simgesinin üzerine gelindiğinde ek açıklamanın metni görüntülenir.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Etkinliğin tasarımcısında ek açıklama görüntüleme

1. Etkinliğin dışında görüntülenen ek açıklamasına sahip bir etkinlik Tasarımcısı ile ek açıklama donatıcının **sabitleme** simgesine tıklayın.

   Ek açıklama etkinliğin tasarımcısında görüntülenir. Aşağıdaki ekran görüntüsünde, Etkinlik tasarımcısında "iş akışında başlangıç etkinliği" ek açıklaması görüntülenir.

   ![Etkinlik tasarımcısında gösterilen ek açıklama](../workflow-designer/media/annotationindesigner.png)

2. Ek açıklamayı etkinliğin tasarımcısının dışında göstermek için etkinliğin tasarımcısında ek açıklama alanının üzerine gelin ve **Ayır** simgesine tıklayın

   ![Etkinliğin tasarımcısının dışında görünen ek açıklama](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Tüm ek açıklamaları gösterme veya gizleme

1. Ek açıklamasına sahip bir etkinliğe sağ tıklayın. **Ek açıklamaları**seç, **tüm ek açıklamaları göster**.

   Tüm ek açıklamalar etkinliğin tasarımcıları içinde görüntülenir.

1. Etkinliğin tasarımcıları dışındaki tüm ek açıklamaları göstermek için, etkinliğe sağ tıklayın ve **ek açıklamalar**' ı seçin, **tüm ek açıklamaları gizleyin**.

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Etkinlik için ek açıklama ekleme veya silme

1. Ek açıklamasına sahip bir etkinliğe sağ tıklayın.

1. **Ek açıklamaları**seç, **ek açıklamayı Düzenle** veya **ek açıklamayı Sil**.

   Ek açıklama, düzenlenmek veya silinmek üzere açıldı.

1. Tüm ek açıklamaları aynı anda silmek için, iş akışı tasarımcısına sağ tıklayın ve **ek açıklama**' yı seçin, **tüm ek açıklamaları silin**.

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Bir değişken veya bağımsız değişken için ek açıklama ekleme, düzenlememe ve silme

1. Bir değişkene veya bağımsız değişkene sağ tıklayın ve ek açıklama ekle ' yi seçin.

1. Ek açıklamanın metnini girin. Değişken veya bağımsız değişken bir ek açıklama simgesi görüntüler.

1. Ek açıklamasına sahip bir değişkene veya bağımsız değişkene sağ tıklayın. Ek açıklamayı Düzenle ' yi seçin.

   Ek açıklama düzenlenmek üzere açıldı.

1. Ek açıklamasına sahip bir değişkene veya bağımsız değişkene sağ tıklayın. Ek açıklamayı Sil ' i seçin.

   Ek açıklama silinir.

---
title: 'Nasıl yapılır: İş Akışı Tasarımcısı bir iş akışına yorum ekleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
caps.latest.revision: 7
author: steved0x
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d775c79cc7abdf6a66b1174ae625ca468f0764fc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72663458"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısında bir iş akışına açıklama ekleme
Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için, [!INCLUDE[net_v45](../includes/net-v45-md.md)] geliştiricinin tasarımcıda aşağıdaki öğe türlerine ek açıklamalar eklemesine izin verir:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Türetilmiş sınıflar <xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Ek açıklamanın içerikleri, iş akışıyla ilişkili XAML dosyasına düz metin olarak kaydedilir ve başkaları tarafından okunabilir. Hassas bilgileri bir ek açıklamaya girerken dikkatli olun.

### <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Tasarımcıda bir etkinliğe ek açıklama ekleme

1. İş akışı tasarımcısında, iş akışı tasarımcısında bir öğeye sağ tıklayın ve **ek** **Açıklama Ekle**' yi seçin.

2. Ek açıklamanın metnini, girilen alana ekleyin.

3. Öğe bir ek açıklama simgesi gösterir. Ek açıklama simgesinin üzerine gelindiğinde ek açıklamanın metni görüntülenir.

     ![Ek açıklamayı gösteren sıralı etkinlik](../workflow-designer/media/annotation.png "Ek Açıklama")

### <a name="displaying-an-annotation-in-an-activitys-designer"></a>Etkinliğin tasarımcısında ek açıklama görüntüleme

1. Etkinliğin dışında görüntülenen ek açıklamasına sahip bir etkinlik Tasarımcısı ile ek açıklama donatıcının **sabitleme** simgesine tıklayın.

2. Ek açıklama etkinliğin tasarımcısında görüntülenir. Aşağıdaki ekran görüntüsünde, Etkinlik tasarımcısında "iş akışında başlangıç etkinliği" ek açıklaması görüntülenir.

     ![Etkinlik tasarımcısında gösterilen ek açıklama](../workflow-designer/media/annotationindesigner.png "Annotationındeimzalayan")

3. Ek açıklamayı etkinliğin tasarımcısının dışında göstermek için etkinliğin tasarımcısında ek açıklama alanının üzerine gelin ve **Ayır** simgesine tıklayın

     ![Etkinliğin designe dışında görünen ek açıklama](../workflow-designer/media/annotationoutsidedesigner.png "AnnotationOutsideDesigner")

### <a name="showing-or-hiding-all-annotations"></a>Tüm ek açıklamaları gösterme veya gizleme

1. Ek açıklamasına sahip bir etkinliğe sağ tıklayın. **Ek açıklamaları**seç, **tüm ek açıklamaları göster**.

2. Tüm ek açıklamalar etkinliğin tasarımcıları içinde görüntülenir.

3. Etkinliğin tasarımcıları dışındaki tüm ek açıklamaları göstermek için, etkinliğe sağ tıklayın ve **ek açıklamalar**' ı seçin, **tüm ek açıklamaları gizleyin**.

### <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Etkinlik için ek açıklama ekleme veya silme

1. Ek açıklamasına sahip bir etkinliğe sağ tıklayın.

2. **Ek açıklamaları**seç, **ek açıklamayı Düzenle** veya **ek açıklamayı Sil**.

3. Ek açıklama, düzenlenmek üzere açılacak veya silinecek.

4. Tüm ek açıklamaları aynı anda silmek için, iş akışı tasarımcısına sağ tıklayın ve **ek açıklama**' yı seçin, **tüm ek açıklamaları silin**.

### <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Bir değişken veya bağımsız değişken için ek açıklama ekleme, düzenlememe ve silme

1. Bir değişkene veya bağımsız değişkene sağ tıklayın ve ek açıklama ekle ' yi seçin.

2. Ek açıklamanın metnini girin. Değişken veya bağımsız değişken, bir ek açıklama simgesi görüntüler.

3. Ek açıklamasına sahip bir değişkene veya bağımsız değişkene sağ tıklayın. Ek açıklamayı Düzenle ' yi seçin.

4. Ek açıklama düzenlenmek üzere açılacak.

5. Ek açıklamasına sahip bir değişkene veya bağımsız değişkene sağ tıklayın. Ek açıklamayı Sil ' i seçin.

6. Ek açıklama silinir.
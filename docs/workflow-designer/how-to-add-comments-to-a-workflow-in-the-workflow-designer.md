---
title: 'İş Akışı Tasarımcısı - Nasıl kullanılır: İş akışına açıklama ekleme'
description: 4.5 .NET Framework geliştiricinin tasarımcıdaki belirli öğe türlerine (etkinlik, durum ve geçiş öğeleri gibi) ek açıklamalar eklemesine nasıl izin verir?
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
f1_keywords:
- System.Activities.Presentation.Annotations.Annotation.UI
- Annotation
ms.assetid: 9aa0e8d6-8129-4438-8389-d460611581a7
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
author: TerryGLee
ms.openlocfilehash: 81de5a8b27626066fb8c85b5d13da2f387bae8c9
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963744"
---
# <a name="how-to-add-comments-to-a-workflow-in-the-workflow-designer"></a>Nasıl yapılır: İş Akışı Tasarımcısında bir iş akışına açıklama ekleme

Daha büyük, daha karmaşık iş akışları oluşturmayı kolaylaştırmak için .NET Framework 4.5, geliştiricinin tasarımcıda aşağıdaki öğe türlerine ek açıklamalar eklemesine olanak sağlar:

- <xref:System.Activities.Activity>

- <xref:System.Activities.Statements.State>

- <xref:System.Activities.Statements.Transition>

- Türetilen sınıflar <xref:System.Activities.Statements.FlowNode>

- <xref:System.Activities.Variable>

- <xref:System.Activities.Argument>

> [!IMPORTANT]
> Ek açıklamanın içeriği iş akışıyla ilişkili XAML dosyasına düz metin olarak kaydedilir ve muhtemelen başkaları tarafından okunabilir. Bir ek açıklamaya hassas bilgiler girerken dikkatli olun.

## <a name="adding-an-annotation-to-an-activity-in-the-designer"></a>Tasarımcıda bir etkinliğin ek açıklamasını ekleme

1. İş akışı tasarımcısında, iş akışı tasarımcısında bir öğeye sağ tıklayın ve Ek Açıklamalar , Ek **Açıklama** **Ekle'yi seçin.**

1. Ek açıklama metnini sağlanan alana ekleyin.

   Öğe bir ek açıklama simgesi gösterir. Ek açıklama simgesinin üzerine gelindiğinde ek açıklama metni görüntülenir.

## <a name="displaying-an-annotation-in-an-activitys-designer"></a>Bir etkinliğin tasarımcısında ek açıklama görüntüleme

1. Etkinliğin dışında bir ek açıklama görüntüleyen etkinlik tasarımcısında, ek **açıklama** donatıcıda Sabitle simgesine tıklayın.

   Ek açıklama, etkinliğin tasarımcısında görüntülenir. Aşağıdaki ekran görüntüsünde, etkinliğin tasarımcısında "İş akışında etkinlik başlat" ek açıklaması görüntülenir.

   ![Etkinlik tasarımcısında gösterilen ek açıklama](../workflow-designer/media/annotationindesigner.png)

2. Ek açıklamayı etkinliğin tasarımcısının dışında görüntülemek için, etkinliğin tasarımcısında ek açıklama alanı üzerine gelin ve Sonra Dalı Çıkar **simgesine** tıklayın

   ![Bir etkinliğin tasarımcısı dışında görüntülenen ek açıklama](../workflow-designer/media/annotationoutsidedesigner.png)

## <a name="showing-or-hiding-all-annotations"></a>Tüm ek açıklamaları gösterme veya gizleme

1. Ek açıklaması olan bir etkinliği sağ tıklayın. Ek **Açıklamalar'ı,** **Tüm Ek Açıklamaları Göster'i seçin.**

   Tüm ek açıklamalar etkinliğin tasarımcılarında görüntülenir.

1. Etkinliğin tasarımcıları dışındaki tüm ek açıklamaları görüntülemek için, etkinlike sağ tıklayın ve Ek Açıklamalar **'ı** seçin, Tüm Ek **Açıklamaları Gizle'yi seçin.**

## <a name="editing-or-deleting-an-annotation-for-an-activity"></a>Bir etkinlik için ek açıklamayı düzenleme veya silme

1. Ek açıklaması olan bir etkinlikte sağ tıklayın.

1. Ek **Açıklamalar, Ek Açıklamayı** **Düzenle veya Ek** **Açıklamayı Sil'i seçin.**

   Ek açıklama düzenleme veya silme için açılır.

1. Tüm ek açıklamaları aynı anda silmek için iş akışı tasarımcısına sağ tıklayın ve Ek Açıklama **,** Tüm Ek **Açıklamaları Sil'i seçin.**

## <a name="adding-editing-and-deleting-an-annotation-for-a-variable-or-argument"></a>Değişken veya bağımsız değişken için ek açıklama ekleme, düzenleme ve silme

1. Bir değişkene veya bağımsız değişkene sağ tıklayın ve Ek Açıklama Ekle'yi seçin.

1. Ek açıklamanın metnini girin. Değişken veya bağımsız değişken bir ek açıklama simgesi görüntüler.

1. Ek açıklaması olan bir değişkene veya bağımsız değişkene sağ tıklayın. Ek Açıklamayı Düzenle'yi seçin.

   Ek açıklama düzenleme için açılır.

1. Ek açıklaması olan bir değişkene veya bağımsız değişkene sağ tıklayın. Ek Açıklamayı Sil'i seçin.

   Ek açıklama silinir.

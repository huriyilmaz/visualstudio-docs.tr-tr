---
title: 'İş Akışı Tasarımcısı: İş akışı projesine yeni öğe ekleme'
description: İş akışı projesi oluşturduktan sonra projenize iş akışı etkinlikleri, tasarımcılar ve Visual Studio iş akışı öğeleri ekleme hakkında bilgi sahibi olun.
ms.custom: SEO-VS-2020
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-workflow-designer
ms.workload:
- multiple
ms.openlocfilehash: d09699c345878d27eecba518c54f8ff0cfd44d1b
ms.sourcegitcommit: 0841d3f610bd2af4af1cf07dd9d31d1e0629b193
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/09/2021
ms.locfileid: "123963743"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Nasıl kullanılır: İş akışı projesine yeni öğe ekleme

Bir iş akışı projesi oluşturduktan sonra iş akışı etkinliklerini, tasarımcıları ve diğer tanıdık Visual Studio öğeleri projenize ebilirsiniz.

Aşağıdaki tabloda bir Windows workflow Foundation (WF) öğelerinin listesi ve ardından aşağıdaki tabloda yer alır:

| Ad | Açıklama |
|-| - |
| Etkinlik | Diğer etkinliklerden oluşan bir etkinlik. Bu öğenin seçimi, yeni bir proje için Etkinlik Kitaplığı şablonunu  seçerek elde etmek istediğiniz XAML dosyasını projeye ekler. Bu yordam hakkında daha fazla bilgi için [bkz. İş akışı projesi oluşturma.](creating-a-workflow-project.md) |
| Etkinlik Tasarımcısı | Bir etkinliğin tasarım zamanı deneyimini özelleştirmek için tasarımcı. Bu öğenin seçimi, yeni bir proje için Etkinlik Tasarımcısı Kitaplığı şablonunu seçerken elde **edilenlerle** aynı dosyaları projeye ekler. |
| Kod Etkinliği | Kodla yazılmış yürütme mantığına sahip bir etkinlik. Yöntemi geçersiz kılma ile bir kaynak <xref:System.Activities.CodeActivity.Execute%2A> kod dosyası sizin için zaten oluşturulmuş. |
| WCF İş Akışı Hizmeti | İş [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)] akışı etkinlikleri kullanılarak bir hizmet. Bu öğenin seçimi, yeni bir proje için **WCF** İş Akışı Hizmeti Uygulaması şablonunu seçerek elde edilen dosyaları projeye ekler. Bu yordam hakkında daha fazla bilgi için, [bkz. How to: Create a WCF Workflow Service Application](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>bir iş akışı projesine yeni öğe eklemek için

1. Yeni **Project** **Ekle'yi seçin.**

   Yeni **Öğe Ekle iletişim** kutusu açılır.

1. Sol bölmede İş akışı **kategorisini ve** ardından bir iş akışı öğesi şablonu seçin.

   > [!NOTE]
   > İş Akışı kategorisini **görmüyorsanız,** önce Windows **Workflow Foundation** bileşenini Visual Studio. Ayrıntılı yönergeler için bkz. [Workflow Foundation Windows yükleme.](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation)

1. İletişim kutusunun altındaki Ad **kutusuna** öğe için bir ad girin.

1. Öğeyi **projeye** eklemek için Ekle'yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş akışı projesi oluşturma](../workflow-designer/creating-a-workflow-project.md)

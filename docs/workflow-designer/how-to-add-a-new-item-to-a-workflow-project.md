---
title: 'İş Akışı Tasarımcısı: iş akışı projesine yeni öğe ekleme'
ms.date: 06/25/2018
ms.topic: how-to
ms.assetid: 5c6180ca-af10-4513-b0cb-7d478fd84eab
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 53737eb421f4194b00354899e373441ff0a97227
ms.sourcegitcommit: ca777040ca372014b9af5e188d9b60bf56e3e36f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85814622"
---
# <a name="how-to-add-a-new-item-to-a-workflow-project"></a>Nasıl yapılır: bir iş akışı projesine yeni öğe ekleme

Bir iş akışı projesi oluşturduktan sonra, iş akışı etkinliklerini, tasarımcıları ve diğer tanıdık Visual Studio öğelerini projenize ekleyebilirsiniz.

Aşağıdaki tabloda, bir iş akışı projesine ekleyebileceğiniz Windows Workflow Foundation (WF) öğeleri listelenmektedir:

| Name | Açıklama |
|-| - |
| Etkinlik | Diğer etkinliklerden oluşan etkinlik. Bu öğenin seçilmesi, yeni bir proje için **etkinlik kitaplığı** şablonunu seçerken elde ettiğiniz xaml dosyasını projeye ekler. Bu yordam hakkında daha fazla bilgi için bkz. [iş akışı projesi oluşturma](creating-a-workflow-project.md). |
| Etkinlik Tasarımcısı | Bir etkinliğin tasarım zamanı deneyimini özelleştirmek için bir tasarımcı. Bu öğe seçildiğinde, yeni bir proje için **etkinlik Tasarımcısı kitaplık** şablonunu seçerken elde ettiğiniz dosyalar projeye eklenir. |
| Kod etkinliği | Yürütme mantığı kod olarak yazılmış bir etkinlik. Metodu için geçersiz kılma içeren bir kaynak kodu dosyası <xref:System.Activities.CodeActivity.Execute%2A> zaten oluşturuldu. |
| WCF Iş akışı hizmeti | [!INCLUDE[indigo2](../workflow-designer/includes/indigo2_md.md)]İş akışı etkinlikleri kullanılarak oluşturulan bir hizmet. Bu öğe seçildiğinde, yeni bir proje için **WCF Iş akışı hizmeti uygulama** şablonunu seçerken elde ettiğiniz dosyalar projeye eklenir. Bu yordam hakkında daha fazla bilgi için bkz. [nasıl yapılır: WCF Iş akışı hizmeti uygulaması oluşturma](creating-a-workflow-project.md). |

## <a name="to-add-a-new-item-to-a-workflow-project"></a>Bir iş akışı projesine yeni bir öğe eklemek için

1. **Proje** menüsünde **Yeni öğe Ekle**' yi seçin.

   **Yeni öğe Ekle** iletişim kutusu açılır.

1. Sol bölmede, **Iş akışı** kategorisini seçin ve sonra bir iş akışı öğesi şablonu seçin.

   > [!NOTE]
   > **Iş akışı** kategorisini görmüyorsanız, önce Visual Studio 'nun **Windows Workflow Foundation** bileşenini yüklemeniz gerekir. Ayrıntılı yönergeler için bkz. [ınstall Windows Workflow Foundation](developing-applications-with-the-workflow-designer.md#install-windows-workflow-foundation).

1. İletişim kutusunun alt kısmındaki **ad** kutusuna öğe için bir ad girin.

1. Öğeyi projeye eklemek için **Ekle** ' yi seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [İş akışı projesi oluşturma](../workflow-designer/creating-a-workflow-project.md)

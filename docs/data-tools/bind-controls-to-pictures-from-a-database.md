---
title: Bir veritabanından resimlere denetim bağlama
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- images [Visual Basic], displaying on Windows Forms
- data binding [Windows Forms], pictures
- images [Visual Basic], data binding
- pictures, data binding
- pictures, dragging from Data Sources window
- Data Sources Window, setting controls to display images
- PictureBox control [Windows Forms], data binding
- images [Visual Basic], dragging from Data Sources window
ms.assetid: 9748815e-3556-49e8-86b1-c6aa593c6163
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 64168339e5f6bd9be6b3108268a009f6a87bc22c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72648826"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Bir veritabanından resimlere denetim bağlama

**Veri kaynakları** penceresini, bir veritabanındaki bir görüntüyü uygulamanızdaki bir denetime bağlamak için kullanabilirsiniz. Örneğin, bir görüntüyü WPF uygulamasında bir <xref:System.Windows.Controls.Image> denetimine veya Windows Forms uygulamasındaki bir <xref:System.Windows.Forms.PictureBox> denetimine bağlayabilirsiniz.

Veritabanındaki resimler genellikle bayt dizileri olarak depolanır. Byte dizileri olarak depolanan **veri kaynakları** penceresindeki öğelerin denetim türü varsayılan olarak **none** olarak ayarlanmış, çünkü byte dizileri, basit bir bayt dizisinden büyük bir uygulamanın yürütülebilir dosyasına herhangi bir şey içerebildiğinden. Bir görüntüyü temsil eden **veri kaynakları** penceresinde bir bayt dizisi öğesi için veri bağlantılı bir denetim oluşturmak için, oluşturulacak denetimi seçmeniz gerekir.

Aşağıdaki yordamda, **veri kaynakları** penceresinin görüntenize bağlanan bir öğeyle zaten doldurulmuş olduğu varsayılır.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Veritabanında bir resmi bir denetime bağlamak için

1. Denetimi eklemek istediğiniz tasarım yüzeyinin WPF Tasarımcısında veya Windows Form Tasarımcısı açık olduğundan emin olun.

2. **Veri kaynakları** penceresinde, sütun veya özelliklerini göstermek için istenen tabloyu veya nesneyi genişletin.

   > [!TIP]
   > **Veri kaynakları** penceresi açık değilse,**diğer Windows**  > **veri kaynaklarını** **görüntüle**  >  ' yi seçerek açın.

3. Görüntü verilerinizi içeren sütunu veya özelliği seçin ve açılan denetim listesinden aşağıdaki denetimlerden birini seçin:

    - WPF Tasarımcısı açıksa **görüntü**' i seçin.

    - Windows Forms Tasarımcısı açıksa, **PictureBox**' ı seçin.

    - Alternatif olarak, veri bağlamayı destekleyen ve görüntü görüntüleyebilen farklı bir denetim seçebilirsiniz. Kullanmak istediğiniz denetim kullanılabilir denetimler listesinde değilse, listeye ekleyebilir ve sonra bunu seçebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)
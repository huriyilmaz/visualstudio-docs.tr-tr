---
title: Bir veritabanından resimlere denetim bağlama
description: Veri Kaynakları penceresini kullanarak veritabanındaki bir görüntüyü veri kaynağı uygulamanıza Visual Studio bağlayın.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
author: ghogen
ms.author: ghogen
manager: jmartens
ms.technology: vs-data-tools
ms.workload:
- data-storage
ms.openlocfilehash: f1f1db5a2d98b6e55b0da97e7550bc33698ff072
ms.sourcegitcommit: b12a38744db371d2894769ecf305585f9577792f
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/13/2021
ms.locfileid: "126631592"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Bir veritabanından resimlere denetim bağlama

Veri Kaynakları penceresini **kullanarak veritabanındaki** bir görüntüyü uygulamanıza bir denetime bebilirsiniz. Örneğin, bir görüntüyü WPF uygulamasındaki bir <xref:System.Windows.Controls.Image> denetime veya Windows <xref:System.Windows.Forms.PictureBox> Forms uygulamasındaki bir denetime bebilirsiniz.

Bir veritabanındaki resimler genellikle byte dizileri olarak depolanır. Bayt **dizileri olarak** depolanan Veri Kaynakları penceresindeki öğelerin denetim  türü varsayılan olarak Yok olarak ayarlanır, çünkü bayt dizileri basit bir bayt dizisinde büyük bir uygulamanın yürütülebilir dosyasına kadar her şeyi içerebilir. Veri Kaynakları penceresinde bir görüntüyü temsil eden bir  byte dizisi öğesi için veriye bağlı bir denetim oluşturmak için, oluşturmak istediğiniz denetimi seçmeniz gerekir.

Aşağıdaki yordam, Veri Kaynakları **penceresinin görüntünüze** bağlı bir öğeyle zaten doldurulduğundan emin olur.

## <a name="to-bind-a-picture-in-a-database-to-a-control"></a>Veritabanındaki bir resmi denetime bağlamak için

1. Denetimi eklemek istediğiniz tasarım yüzeyinin WPF Tasarımcısı'nda veya Windows Forms Designer'da açık olduğundan emin olun.

2. Veri Kaynakları **penceresinde,** sütunlarını veya özelliklerini görüntülemek için istenen tabloyu veya nesneyi genişletin.

   > [!TIP]
   > Veri **Kaynakları penceresi açık** değilse Diğer Veri Kaynaklarını Görüntüle'yi **seçerek**  >  **Windows**  >  **açın.**

3. Görüntü verilerinizi içeren sütunu veya özelliği seçin ve açılan denetim listesinden aşağıdaki denetimlerden birini seçin:

    - WPF tasarımcısı açıksa Görüntü'leri **seçin.**

    - Windows Forms tasarımcısı açıksa **PictureBox'ı seçin.**

    - Alternatif olarak, veri bağlamayı destekleyen ve görüntüleri görüntüleyen farklı bir denetim de seçebilirsiniz. Kullanmak istediğiniz denetim kullanılabilir denetim listesinde yer alıyorsa, bunu listeye ekleyebilir ve ardından seçebilirsiniz. Daha fazla bilgi için [Bkz. Veri Kaynakları penceresine özel denetimler ekleme.](../data-tools/add-custom-controls-to-the-data-sources-window.md)

## <a name="see-also"></a>Ayrıca bkz.

- [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio.md)

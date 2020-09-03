---
title: Denetimleri bir veritabanından resimlere bağlama | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
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
caps.latest.revision: 18
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 0b8f6ee192399c8af8a508b2f9c2817db954bb36
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72673009"
---
# <a name="bind-controls-to-pictures-from-a-database"></a>Bir veritabanından resimlere denetim bağlama
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

**Veri kaynakları** penceresini, bir veritabanındaki bir görüntüyü uygulamanızdaki bir denetime bağlamak için kullanabilirsiniz. Örneğin, bir görüntüyü <xref:System.Windows.Controls.Image> WPF uygulamasında bir denetime veya <xref:System.Windows.Forms.PictureBox> Windows Forms uygulamasındaki bir denetime bağlayabilirsiniz.

 Veritabanındaki resimler genellikle bayt dizileri olarak depolanır. Byte dizileri olarak depolanan **veri kaynakları** penceresindeki öğelerin denetim türü varsayılan olarak **none** olarak ayarlanmış, çünkü byte dizileri, basit bir bayt dizisinden büyük bir uygulamanın yürütülebilir dosyasına herhangi bir şey içerebildiğinden. Bir görüntüyü temsil eden **veri kaynakları** penceresinde bir bayt dizisi öğesi için veri bağlantılı bir denetim oluşturmak için, oluşturulacak denetimi seçmeniz gerekir.

 Aşağıdaki yordamda, **veri kaynakları** penceresinin görüntenize bağlanan bir öğeyle zaten doldurulmuş olduğu varsayılır.

## <a name="bind-a-picture-in-a-database-to-a-control"></a>Veritabanında bir resmi bir denetime bağlama

1. Denetimi eklemek istediğiniz tasarım yüzeyinin WPF Tasarımcısında veya Windows Form Tasarımcısı açık olduğundan emin olun.

2. **Veri kaynakları** penceresinde, sütun veya özelliklerini göstermek için istenen tabloyu veya nesneyi genişletin.

3. Görüntü verilerinizi içeren sütunu veya özelliği seçin ve açılan denetim listesinden aşağıdaki denetimlerden birini seçin:

    - WPF Tasarımcısı açıksa **görüntü**' i seçin.

    - Windows Forms Tasarımcısı açıksa, **PictureBox**' ı seçin.

    - Alternatif olarak, veri bağlamayı destekleyen ve görüntü görüntüleyebilen farklı bir denetim seçebilirsiniz. Kullanmak istediğiniz denetim kullanılabilir denetimler listesinde değilse, listeye ekleyebilir ve sonra bunu seçebilirsiniz. Daha fazla bilgi için bkz. [veri kaynakları penceresine özel denetimler ekleme](../data-tools/add-custom-controls-to-the-data-sources-window.md).

## <a name="see-also"></a>Ayrıca Bkz.
 [Visual Studio'da verilere WPF denetimleri bağlama](../data-tools/bind-wpf-controls-to-data-in-visual-studio1.md)

---
title: 'Nasıl yapılır: bağımsız değişken tasarımcısını kullanma | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-workflow-designer
ms.topic: reference
f1_keywords:
- System.Activities.Presentation.View.ArgumentDesigner.UI
- System.Activities.Presentation.View.DesignTimeArgument.UI
ms.assetid: 64813fd5-1ea1-499a-98b4-ab2a44b7ee5e
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: a436d33bbb7c791f3f192357fded779fa77d148d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72659109"
---
# <a name="how-to-use-the-argument-designer"></a>Nasıl yapılır: bağımsız değişken tasarımcısını kullanma
@No__t_0 önceki sürümleriyle karşılaştırıldığında, bağımsız değişken Tasarımcısı verilerin bir etkinliğin içine ve dışına akmasını kolaylaştırır. Tasarımcı, tasarım tuvalinin sol alt köşesindeki **bağımsız değişkenler** düğmesine tıklanarak erişilir. Tasarımcı, tablo biçiminde görüntülenen bağımsız değişkenlerin bir listesini içerir ve **varsayılan değer** sütunu dışında her bir sütun üst bilgisi tarafından sıralanabilir. Her bağımsız değişken bir ad, ın/out/out/Property Direction, Type ve varsayılan ifade değeri (varsa) içerir. Ad ve varsayılan ifade değeri, düzenlenebilir metin alanlarıdır ve tür ve yönün açılan listeleri vardır. bağımsız değişkenler [!INCLUDE[crabout](../includes/crabout-md.md)], bkz. [değişkenler ve bağımsız değişkenler](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8).

### <a name="to-create-a-new-argument"></a>Yeni bir bağımsız değişken oluşturmak için

1. @No__t_0 bir iş akışı veya etkinlik çözümü açın.

2. Tasarım tuvalinin sol alt köşesindeki **bağımsız değişkenler** düğmesine tıklayarak bağımsız değişkenler tasarımcısını açın. Bağımsız değişkenler Tasarımcısı görüntülenir.

3. **Oluşturma bağımsız değişkeni**etiketli boş satıra tıklayın. Bu işlem, aşağıdaki varsayılan değerleri kullanarak yeni bir bağımsız değişken içeren yeni bir satır ekler: x olarak, benzersiz bağımsız değişken adları oluşturmak için otomatik olarak arttırılan 1 başlangıç değeri, **yönü** **için,** **bağımsız değişken türü**için **dize** . **Varsayılan değer**için hiçbir değer eklenmez. Bu değerleri, iş akışı tasarım sürecinde istediğiniz zaman değiştirebilirsiniz.

    > [!NOTE]
    > Bir bağımsız değişkeni silmek için, ve ardından **Delete** tuşuna basarak bağımsız değişkeni seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [İş akışı Tasarımcısı](../workflow-designer/using-the-workflow-designer.md) [değişkenlerini ve bağımsız değişkenleri](https://msdn.microsoft.com/library/d03dbe34-5b2e-4f21-8b57-693ee49611b8) kullanma
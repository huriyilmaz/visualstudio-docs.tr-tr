---
title: 'Nasıl |: Özellik | Microsoft Docs'
description: Sabit kodlu dize değerlerini yerelleştirilmiş kaynaklara başvurulan ifadelerle değiştirerek SharePoint başlıklarını ve açıklamalarını yerelleştirmeyi öğrenin.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: how-to
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- features [SharePoint development in Visual Studio]
- SharePoint development in Visual Studio, localizing
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.technology: sharepoint-development
ms.workload:
- office
ms.openlocfilehash: bbce7034434051690dad7ee3c54d83498f200ab4
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122047614"
---
# <a name="how-to-localize-a-feature"></a>Nasıl: Bir özelliği yerelleştirme
  Varsayılan olarak, özellik başlıkları ve açıklamalar sabit kodlu dize değerleri kullanır. Özellik başlığını ve açıklamasını yerelleştirmek için dizeleri yerelleştirilmiş kaynaklara başvurulan ifadelerle değiştirin.

## <a name="localize-a-feature"></a>Özelliği yerelleştirme

#### <a name="to-localize-a-feature"></a>Bir özelliği yerelleştirmek için

1. Bu **Çözüm Gezgini** Özellik1 düğümünün **kısayol** menüsünü açın ve Özellik Kaynağı **Ekle'yi seçin.**

2. Kaynak **Ekle iletişim** kutusunda, varsayılan dil **özelliği kaynak** dosyası için kültür olarak listeden Sabit Dil'i seçin.

3. Yerelleştirilmiş her dil için önceki adımı yineler ve yerelleştirilmiş özellik kaynak dosyaları için seçtiğiniz dilleri seçin.

     Ayrı özellik kaynak dosyaları oluşturulur: varsayılan dil için bir tane ve desteklemek istediğiniz her yerelleştirilmiş dil için bir tane.

4. Kaynak Düzenleyicisi'nde her bir kaynak dosyasını açın ve ardından tüm dize kimliklerini ve değerlerini girin.

     Örneğin, varsayılan özellik kaynak dosyasında, Özellik Başlığım değerine sahip başlık dize kimliğini ve  Özelliğim Açıklaması değeriyle Açıklama'nın ikinci dize **kimliğini girin.**  Yerelleştirilmiş her kaynak dosyası için, varsayılan özellik kaynağında kullanılan dize kimliklerini kullanın, ancak değerler için yerelleştirilmiş dizeler girin.

5. Tüm kaynak değerlerini girdikten sonra, özelliğin kısayol menüsünü açın *(örneğin, Feature1.feature)* ve Görünüm Tasarımcısı'ı seçen özellik Tasarımcısı'nda açın. 

6. Özellikte Başlık **ve Açıklama** **alanlarını** yerelleştirmek için, kutularına değer girmek için aşağıdaki biçimi kullanın:

     `$Resources:`*Dize Kimliği*

     Örneğin, özellik $Resources:**Başlık** yazın  ve $Resources: **Açıklama'ya** tıklayın.

     Dize kimlikleri, kaynak dosyalarında kullanılan kimliklerle eşleşmeli.

7. Uygulamayı **derlemek ve** çalıştırmak için F5 anahtarını seçin.

8. Bu SharePoint **Site Eylemleri** menüsünü açın, **Site** Ayarlar'ı seçin ve **ardından Site Eylemleri** bölümünde Site Özelliklerini Yönet **bağlantısını** seçin.

9. Bu SharePoint varsayılandan görüntüleme dilini değiştirebilirsiniz.

     Yerelleştirilmiş özellik başlığı ve açıklaması uygulamada görünür. Yerelleştirilmiş kaynakları görüntülemek için SharePoint sunucusunda kaynak dosyasının kültürüyle eşleşen bir dil paketi yüklü olması gerekir.

## <a name="see-also"></a>Ayrıca bkz.
- [Yerelleştirme SharePoint yerelleştirme](../sharepoint/localizing-sharepoint-solutions.md)
- [Nasıl: Kaynak dosyası ekleme](../sharepoint/how-to-add-a-resource-file.md)
- [Nasıl yapabilirsiniz: ASPX işaretlemeyi yerelleştirme](../sharepoint/how-to-localize-aspx-markup.md)
- [Nasıl olur: Kodu yerelleştirme](../sharepoint/how-to-localize-code.md)

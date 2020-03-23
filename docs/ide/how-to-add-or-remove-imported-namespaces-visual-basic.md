---
title: 'Nasıl yapılır: İçe aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)'
ms.date: 06/21/2017
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e636969164c4cf2526bb85add95e7cfe02ce6176
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593336"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Nasıl yapılır: İçe aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)

Ad alanı almak, öğeyi tam olarak nitelemeden kodunuzda ki ad alanından öğeleri kullanmanıza olanak tanır. `Create` Örneğin, `System.Messaging.MessageQueue` sınıftaki yönteme erişmek istiyorsanız, `System.Messaging` ad alanını içe aktarabilir ve kodda gereksinim duyduğunuz öğeye `MessageQueue.Create`".

Alınan ad alanları **Proje Tasarımcısı'nın** **Başvurular** sayfasında yönetilir. Bu iletişim kutusunda belirttiğiniz içeri aktarımlar doğrudan derleyiciye *(/içe aktarma)* aktarılır ve projenizdeki tüm dosyalara uygulanır. `Imports` Tek bir kaynak kodu dosyasında ad alanı kullanmak için deyimi kullanın.

### <a name="to-add-an-imported-namespace"></a>İçe aktarılan ad alanı eklemek için

1. **Çözüm Gezgini'nde,** proje için **Projem** düğümüne çift tıklayın.

2. Proje **Tasarımcısı'nda,** **Başvurular** sekmesini tıklatın.

3. **İçe Aktarılan Ad Alanları** listesinde, eklemek istediğiniz ad alanının onay kutusunu seçin.

    > [!NOTE]
    > İçe aktarılabilmesi için ad alanının başvurulan bir bileşende olması gerekir. Ad alanı listede görünmüyorsa, onu içeren bileşene bir başvuru eklemeniz gerekir. Daha fazla bilgi için [bkz.](managing-references-in-a-project.md)

### <a name="to-remove-an-imported-namespace"></a>İçe aktarılan ad alanını kaldırmak için

1. **Çözüm Gezgini'nde,** proje için **Projem** düğümüne çift tıklayın.

2. Proje **Tasarımcısı'nda,** **Başvurular** sekmesini tıklatın.

3. **İçe Aktarılan Ad Alanları** listesinde, kaldırmak istediğiniz ad alanının onay kutusunu temizleyin.

## <a name="user-imports"></a>Kullanıcı içeriak
Kullanıcı içeri aktarımları, tüm ad alanı yerine ad alanı içinde belirli bir sınıfı içe aktarmanızı sağlar. Örneğin, uygulamanız <xref:System.Diagnostics> ad alanı için bir alma olabilir, ancak bu ad alanı içinde `Debug` ilgilendiğiniz tek sınıf sınıftır. Kullanıcı alma <xref:System.Diagnostics.Debug> olarak tanımlayabilirsiniz ve sonra <xref:System.Diagnostics>için içe aktarma kaldırın.

Daha sonra fikrinizi değiştirir ve gerçekten `EventLog` ihtiyacınız olan sınıf olduğuna <xref:System.Diagnostics.EventLog> karar verirseniz, <xref:System.Diagnostics.Debug> güncelleştirme işlevini kullanarak kullanıcı alma ve üzerine yazabilirsiniz.

### <a name="to-add-a-user-import"></a>Kullanıcı alma eklemek için

1. **Çözüm Gezgini'nde,** proje için **Projem** düğümüne çift tıklayın.

2. Proje **Tasarımcısı'nda,** **Başvurular** sekmesini tıklatın.

3. **İçe Aktarılan Ad Alanları** listesinin altındaki metin kutusuna, kök ad alanı da dahil olmak üzere almak istediğiniz ad alanının tam adını girin.

4. İçe **Aktarılan Ad Alanları** listesine ad alanını eklemek için kullanıcı alma **ekle** düğmesini tıklatın.

    > [!NOTE]
    > Kullanıcı **alma ekle** düğmesi, ad alanı listede zaten biriyle eşleşirse devre dışı bırakılır; iki kez içe aktarma yapamazsınız.

### <a name="to-update-a-user-import"></a>Kullanıcı alma güncelleştirmek için

1. **Çözüm Gezgini'nde,** proje için **Projem** düğümüne çift tıklayın.

2. Proje **Tasarımcısı'nda,** **Başvurular** sekmesini tıklatın.

3. **İçe Aktarılan Ad Alanları** listesinde, değiştirmek istediğiniz ad alanını seçin.

4. **İçe Aktarılan Ad Alanları** listesinin altındaki metin kutusuna yeni ad alanının adını girin.

5. **İçe Aktarılan Ad Alanları** listesindeki ad alanını güncelleştirmek için **Kullanıcı alma alanını güncelleştir** düğmesini tıklatın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)

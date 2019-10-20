---
title: 'Nasıl yapılır: içeri aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)'
ms.date: 06/21/2017
ms.topic: conceptual
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 8ff6ad1a07440b27b679fa3f749c24a6d3157dbd
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654650"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Nasıl yapılır: içeri aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)

Bir ad alanını içeri aktarmak, öğesini tamamen nitelemeden kodunuzda bu ad alanındaki öğeleri kullanmanıza olanak sağlar. Örneğin, `System.Messaging.MessageQueue` sınıfındaki `Create` yöntemine erişmek istiyorsanız, `System.Messaging` ad alanını içeri aktarabilir ve yalnızca `MessageQueue.Create` olarak kodunuzda ihtiyacınız olan öğeye başvurabilirsiniz.

İçeri aktarılan ad alanları, **Proje Tasarımcısı**'nın **Başvurular** sayfasında yönetilir. Bu iletişim kutusunda belirttiğiniz içeri aktarmalar doğrudan derleyiciye geçirilir ( */Imports*) ve projenizdeki tüm dosyalar için geçerlidir. Tek kaynak kod dosyasında bir ad alanı kullanmak için `Imports` ifadesini kullanın.

### <a name="to-add-an-imported-namespace"></a>İçeri aktarılan bir ad alanı eklemek için

1. **Çözüm Gezgini**, proje Için **projem** düğümüne çift tıklayın.

2. **Proje tasarımcısında**, **Başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinde, eklemek istediğiniz ad alanının onay kutusunu seçin.

    > [!NOTE]
    > İçeri aktarılmak üzere, ad alanı başvurulan bir bileşende olmalıdır. Ad alanı listede görünmezse, onu içeren bileşene bir başvuru eklemeniz gerekir. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>İçeri aktarılan bir ad alanını kaldırma

1. **Çözüm Gezgini**, proje Için **projem** düğümüne çift tıklayın.

2. **Proje tasarımcısında**, **Başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinde, kaldırmak istediğiniz ad alanı için onay kutusunu temizleyin.

## <a name="user-imports"></a>Kullanıcı içeri aktarmaları
Kullanıcı içeri aktarmaları, tüm ad alanı yerine bir ad alanı içinde belirli bir sınıfı içeri aktarmanızı sağlar. Örneğin, uygulamanızda <xref:System.Diagnostics> ad alanı için bir içeri aktarma olabilir, ancak ilgilendiğiniz bu ad alanı içindeki tek sınıf `Debug` sınıfıdır. @No__t_0 Kullanıcı içeri aktarma olarak tanımlayabilir ve sonra <xref:System.Diagnostics> için içeri aktarmayı kaldırabilirsiniz.

Daha sonra fikrinizi değiştirirseniz ve bunun gerçekten gereken `EventLog` sınıfı olduğuna karar verirseniz, Kullanıcı içeri aktarma olarak <xref:System.Diagnostics.EventLog> girebilir ve güncelleştirme işlevini kullanarak <xref:System.Diagnostics.Debug> üzerine yazabilirsiniz.

### <a name="to-add-a-user-import"></a>Kullanıcı içeri aktarma eklemek için

1. **Çözüm Gezgini**, proje Için **projem** düğümüne çift tıklayın.

2. **Proje tasarımcısında**, **Başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinin altındaki metin kutusunda, kök ad alanı dahil olmak üzere içeri aktarmak istediğiniz ad alanının tam adını girin.

4. Ad alanını **Içeri aktarılan ad alanları** listesine eklemek için **Kullanıcı içeri aktarma Ekle** düğmesine tıklayın.

    > [!NOTE]
    > Ad alanı zaten listede bir tane eşleşiyorsa **Kullanıcı içeri aktarma Ekle** düğmesi devre dışı bırakılır; İçeri aktarma 'yi iki kez ekleyemezsiniz.

### <a name="to-update-a-user-import"></a>Bir kullanıcı içeri aktarmayı güncelleştirmek için

1. **Çözüm Gezgini**, proje Için **projem** düğümüne çift tıklayın.

2. **Proje tasarımcısında**, **Başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinde, değiştirmek istediğiniz ad alanını seçin.

4. **Içeri aktarılan ad alanları** listesinin altındaki metin kutusuna yeni ad alanı için bir ad girin.

5. **Içeri aktarılan ad alanları** listesinde ad alanını güncelleştirmek için **Kullanıcı içeri aktarmayı Güncelleştir** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)
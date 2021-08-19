---
title: İçeri aktarılan ad uzaylarını ekleme veya kaldırma (Visual Basic)
description: İçeri aktarılan ad alanlarını ekleme ve kaldırma ve Kullanıcı içeri aktarmaları ekleme veya kaldırma hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.topic: how-to
helpviewer_keywords:
- adding imported namespaces
- removing imported namespaces
- namespaces [Visual Studio], imported
- imported namespaces [Visual Studio]
- references [Visual Studio], imported namespaces
ms.assetid: 44cebec3-0ea0-47c2-8406-4edeab6a997e
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 02af241606b8b8cc4646048b507f3672bf20e4ea
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122101797"
---
# <a name="how-to-add-or-remove-imported-namespaces-visual-basic"></a>Nasıl yapılır: içeri aktarılan ad alanlarını ekleme veya kaldırma (Visual Basic)

Bir ad alanını içeri aktarmak, öğesini tamamen nitelemeden kodunuzda bu ad alanındaki öğeleri kullanmanıza olanak sağlar. Örneğin, `Create` sınıfındaki yöntemine erişmek istiyorsanız `System.Messaging.MessageQueue` , `System.Messaging` ad alanını içeri aktarabilir ve yalnızca kodunuzda gereken öğeye başvurabilirsiniz `MessageQueue.Create` .

içeri aktarılan ad alanları **Project tasarımcısının** **başvurular** sayfasında yönetilir. Bu iletişim kutusunda belirttiğiniz içeri aktarmalar doğrudan derleyiciye geçirilir (*/Imports*) ve projenizdeki tüm dosyalar için geçerlidir. Tek bir `Imports` kaynak kod dosyasında bir ad alanı kullanmak için ifadesini kullanın.

### <a name="to-add-an-imported-namespace"></a>İçeri aktarılan bir ad alanı eklemek için

1. **Çözüm Gezgini**, proje için **Project** düğümüne çift tıklayın.

2. **Project tasarımcısında**, **başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinde, eklemek istediğiniz ad alanının onay kutusunu seçin.

    > [!NOTE]
    > İçeri aktarılmak üzere, ad alanı başvurulan bir bileşende olmalıdır. Ad alanı listede görünmezse, onu içeren bileşene bir başvuru eklemeniz gerekir. Daha fazla bilgi için bkz. [bir projedeki başvuruları yönetme](managing-references-in-a-project.md).

### <a name="to-remove-an-imported-namespace"></a>İçeri aktarılan bir ad alanını kaldırma

1. **Çözüm Gezgini**, proje için **Project** düğümüne çift tıklayın.

2. **Project tasarımcısında**, **başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinde, kaldırmak istediğiniz ad alanı için onay kutusunu temizleyin.

## <a name="user-imports"></a>Kullanıcı içeri aktarmaları
Kullanıcı içeri aktarmaları, tüm ad alanı yerine bir ad alanı içinde belirli bir sınıfı içeri aktarmanızı sağlar. Örneğin, uygulamanız ad alanı için bir içeri aktarmaya sahip olabilir <xref:System.Diagnostics> , ancak ilgilendiğiniz ad alanı içindeki tek sınıf `Debug` sınıfı olur. <xref:System.Diagnostics.Debug>Kullanıcı içeri aktarma olarak tanımlayabilir ve ardından için içeri aktarmayı kaldırabilirsiniz <xref:System.Diagnostics> .

Daha sonra fikrinizi değiştirirseniz ve gerçekten gereken sınıf olduğuna karar verirseniz `EventLog` , <xref:System.Diagnostics.EventLog> Kullanıcı içeri aktarma olarak girebilir ve <xref:System.Diagnostics.Debug> güncelleştirme işlevini kullanarak üzerine yazabilirsiniz.

### <a name="to-add-a-user-import"></a>Kullanıcı içeri aktarma eklemek için

1. **Çözüm Gezgini**, proje için **Project** düğümüne çift tıklayın.

2. **Project tasarımcısında**, **başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinin altındaki metin kutusunda, kök ad alanı dahil olmak üzere içeri aktarmak istediğiniz ad alanının tam adını girin.

4. Ad alanını **Içeri aktarılan ad alanları** listesine eklemek için **Kullanıcı içeri aktarma Ekle** düğmesine tıklayın.

    > [!NOTE]
    > Ad alanı zaten listede bir tane eşleşiyorsa **Kullanıcı içeri aktarma Ekle** düğmesi devre dışı bırakılır; İçeri aktarma 'yi iki kez ekleyemezsiniz.

### <a name="to-update-a-user-import"></a>Bir kullanıcı içeri aktarmayı güncelleştirmek için

1. **Çözüm Gezgini**, proje için **Project** düğümüne çift tıklayın.

2. **Project tasarımcısında**, **başvurular** sekmesine tıklayın.

3. **Içeri aktarılan ad alanları** listesinde, değiştirmek istediğiniz ad alanını seçin.

4. **Içeri aktarılan ad alanları** listesinin altındaki metin kutusuna yeni ad alanı için bir ad girin.

5. **Içeri aktarılan ad alanları** listesinde ad alanını güncelleştirmek için **Kullanıcı içeri aktarmayı Güncelleştir** düğmesine tıklayın.

## <a name="see-also"></a>Ayrıca bkz.

- [Bir projedeki başvuruları yönetme](../ide/managing-references-in-a-project.md)

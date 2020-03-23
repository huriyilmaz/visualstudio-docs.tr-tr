---
title: 'Nasıl yapılı: Yapılandırmalar oluşturma ve düzenleme'
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: conceptual
helpviewer_keywords:
- solution build configurations, editing
- build configurations, creating
- solution build configurations, creating
- build configurations, editing
- builds [Visual Studio], setting up
- property pages
- Configuration Manager
- project build configurations, creating
- project build configurations, editing
ms.assetid: 19be121c-148e-4ece-bbfc-d20b08cfc3f7
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 754d2ceef776ab0dea2d8d51151d4170839173b9
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 03/18/2020
ms.locfileid: "76114705"
---
# <a name="how-to-create-and-edit-configurations"></a>Nasıl yapılı: Yapılandırmalar oluşturma ve düzenleme

Bir çözüm için birkaç yapı yapılandırması oluşturabilirsiniz. Örneğin, test edenlerinizin sorunları bulmak ve gidermek için kullanabileceği bir hata ayıklama yapısı yapılandırabilir ve farklı müşterilere dağıtabileceğiniz farklı türde yapılar yapılandırabilirsiniz.

> [!NOTE]
> Bu konu Windows'daki Visual Studio için geçerlidir. Mac için Visual Studio için Bkz. [Mac için Visual Studio'da yapılandırmaoluştur ve düzenleme yapıl.](/visualstudio/mac/create-and-edit-configurations)

## <a name="create-build-configurations"></a>Yapı yapılandırmaları oluşturma

Varolan yapı yapılandırmalarını seçmek veya değiştirmek veya yeni yapılandırmalar oluşturmak için **Configuration Manager** iletişim kutusunu kullanabilirsiniz.

**Configuration Manager** iletişim kutusunu açmak için **Solution Explorer'da,** çözüm için kısayol menüsünü açın ve ardından Configuration **Manager'ı**seçin.

> [!NOTE]
> Configuration **Manager** komutu kısayol menüsünde görünmüyorsa, menü çubuğundaki **Yapı** menüsünün altına bakın. Menü çubuğunda da görünmüyorsa, **Araçlar** > **Seçenekleri'ni**seçin ve ardından **Seçenekler** iletişim kutusunun sol bölmesinde Projeler **ve Çözümler** > **Genel'i**genişletin ve sağ bölmede Gelişmiş **Yapı yapılandırmalarını göster** onay kutusunu seçin.

Configuration **Manager** iletişim kutusunda, çözüm genelinde bir yapı yapılandırması seçmek, varolan bir yapılandırmayı değiştirmek veya yeni bir yapılandırma oluşturmak için **Etkin çözüm yapılandırma** açılır listesini kullanabilirsiniz. Yapılandırmanın hedeflediğiniz platformu seçmek, varolan bir platformu değiştirmek veya yeni bir platform eklemek için **Etkin çözüm platformu** açılır listesini kullanabilirsiniz. **Proje bağlamları** bölmesi çözümdeki projeleri listeler. Her proje için projeye özgü bir yapılandırma ve platform seçebilir, varolanları değiştirebilir veya yeni bir yapılandırma oluşturabilir veya yeni bir platform ekleyebilirsiniz. Çözümü oluşturmak veya dağıtmak için çözüm genelindeki yapılandırmayı kullandığınızda her projenin dahil edilip edilmeyeceğini belirten onay kutuları da seçebilirsiniz.

İstediğiniz yapılandırmaları ayarladıktan sonra, bu yapılandırmalar için uygun proje özellikleri ayarlayabilirsiniz.

### <a name="set-properties-based-on-configurations"></a>Özellikleri yapılandırmalara göre ayarlama

Özellikleri yapılandırmalara göre ayarlamak için **Çözüm Gezgini'nde,** proje için kısayol menüsünü açın ve ardından **Özellikler'i**seçin. Yapılandırmalarınız için özellikler ayarlayabilirsiniz. Örneğin, bir sürüm yapılandırması için, çözüm oluşturulduğunda kodun en iyi duruma getirilmiş olduğunu belirtebilir ve hata ayıklama yapılandırması için koşullu derleme sembolünün `DEBUG` dahil edildiğini belirtebilirsiniz.

Özellik sayfası ayarları hakkında daha fazla bilgi için [bkz.](../ide/managing-project-and-solution-properties.md)

## <a name="create-a-project-configuration"></a>Proje yapılandırması oluşturma

1. Configuration **Manager** iletişim kutusunu açın.

2. **Proje** sütununda bir proje seçin.

3. Bu projenin **Yapılandırma** açılır listesinde **Yeni'yi**seçin.

     **Yeni Proje Yapılandırmailetişim** kutusu açılır.

4. **Ad** kutusuna, yeni yapılandırma için bir ad girin.

5. Varolan bir proje yapılandırmasından özellik ayarlarını kullanmak için, açılan listeden **kopya ayarlarında** bir yapılandırma seçin.

6. Aynı anda çözüm genelinde bir yapılandırma oluşturmak için **yeni çözüm yapılandırması oluştur** onay kutusunu seçin.

## <a name="rename-a-project-configuration"></a>Proje yapılandırması yeniden adlandırma

1. Configuration **Manager** iletişim kutusunu açın.

2. **Proje** sütununda, yeniden adlandırmak istediğiniz proje yapılandırmasına sahip projeyi seçin.

3. Bu proje için **Yapılandırma** açılır **listesinde, Düzenleme'yi**seçin.

     **Proje Yapılandırmalarını Edit** iletişim kutusu açılır.

4. Değiştirmek istediğiniz proje yapılandırma adını seçin.

5. **Yeniden Adlandır'ı**seçin ve ardından yeni bir ad girin.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Çözüm genelinde yapı yapılandırmaları oluşturma ve değiştirme

### <a name="to-create-a-solution-wide-build-configuration"></a>Çözüm genelinde bir yapı yapılandırması oluşturmak için

1. Configuration **Manager** iletişim kutusunu açın.

2. Etkin **çözüm yapılandırma** açılır listesinde **Yeni'yi**seçin.

     **Yeni Çözüm Yapılandırmailetişim** kutusu açılır.

3. **Ad** metin kutusuna, yeni yapılandırma için bir ad girin.

4. Varolan bir çözüm yapılandırmasından ayarları kullanmak için, açılan listeden **kopya ayarlarında** bir yapılandırma seçin.

5. Proje yapılandırmalarını aynı anda oluşturmak istiyorsanız, **yeni proje yapılandırmaları oluştur** onay kutusunu seçin.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Çözüm genelinde bir yapı yapılandırmasını yeniden adlandırmak için

1. Configuration **Manager** iletişim kutusunu açın.

2. Etkin **çözüm yapılandırma** açılır **listesinde, Düzenleme'yi**seçin.

     **Çözüm Yapılandırmalarını Edit** iletişim kutusu açılır.

3. Değiştirmek istediğiniz çözüm yapılandırma adını seçin.

4. **Yeniden Adlandır'ı**seçin ve ardından yeni bir ad girin.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Çözüm genelindeki yapı yapılandırmasını değiştirmek için

1. Configuration **Manager** iletişim kutusunu açın.

2. Etkin **çözüm yapılandırma** açılır listesinde, istediğiniz yapılandırmayı seçin.

3. Proje **bağlamları** bölmesinde, her proje için istediğiniz **Yapılandırma** ve **Platform'u** seçin ve **oluşturup oluşturmayacağını** ve **dağıtılıp dağıtılmayacağını** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Visual Studio'da projeler ve çözümler oluşturun ve temizleyin](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Yapılandırmalar oluşturma ve düzenleme (Mac için Visual Studio)](/visualstudio/mac/create-and-edit-configurations)

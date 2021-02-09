---
title: 'Nasıl yapılır: yapılandırma oluşturma ve düzenleme'
description: Visual Studio 'Yu kullanarak çözümünüz için birkaç yapı yapılandırması oluşturma ve düzenleme hakkında bilgi edinin.
ms.custom: SEO-VS-2020
ms.date: 06/21/2017
ms.technology: vs-ide-compile
ms.topic: how-to
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 636fbabbede90d9a1c686a2252aef712b4789c18
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99878727"
---
# <a name="how-to-create-and-edit-configurations"></a>Nasıl yapılır: yapılandırma oluşturma ve düzenleme

Bir çözüm için birkaç yapı yapılandırması oluşturabilirsiniz. Örneğin, sınayıcılarınızın sorunları bulmak ve gidermek için kullanabileceği bir hata ayıklama derlemesi yapılandırabilir ve farklı müşterilere dağıtabileceğiniz farklı tür yapılar yapılandırabilirsiniz.

> [!NOTE]
> Bu konu, Windows üzerinde Visual Studio için geçerlidir. Mac için Visual Studio için bkz. [Mac için Visual Studio yapılandırma oluşturma ve düzenleme](/visualstudio/mac/create-and-edit-configurations).

## <a name="create-build-configurations"></a>Derleme yapılandırması oluşturma

**Configuration Manager** iletişim kutusunu, mevcut yapı yapılandırmalarının seçimi veya değiştirilmesi ya da yenilerini oluşturmak için kullanabilirsiniz.

**Configuration Manager** iletişim kutusunu açmak için, **Çözüm Gezgini**' de çözüm için kısayol menüsünü açın ve ardından **Configuration Manager**' yı seçin.

> [!NOTE]
> **Configuration Manager** komutu kısayol menüsünde görünmezse, menü çubuğunda **derleme** menüsünün altına bakın. Burada görünmezse, menü çubuğunda **Araçlar**  >  **Seçenekler**' i seçin ve ardından **Seçenekler** iletişim kutusunun sol bölmesinde, **Projeler ve çözümler**  >  **genel**' i genişletin ve sağ bölmedeki **Gelişmiş derleme yapılandırmasını göster** onay kutusunu seçin.

**Configuration Manager** iletişim kutusunda, çözüm genelinde bir yapı yapılandırması seçmek, var olan bir yapılandırmayı değiştirmek veya yeni bir yapılandırma oluşturmak için **etkin çözüm yapılandırma** açılan listesini kullanabilirsiniz. **Etkin çözüm platformu** açılan listesini, yapılandırmanın hedeflediği platformu seçmek, var olan bir nesneyi değiştirmek veya yeni bir platform eklemek için kullanabilirsiniz. **Proje bağlamları** bölmesinde, çözümdeki projeler listelenir. Her proje için, projeye özgü bir yapılandırma ve platform seçebilir, var olanları değiştirebilir veya yeni bir yapılandırma oluşturabilir ya da yeni bir platform ekleyebilirsiniz. Çözümü derlemek veya dağıtmak için çözüm genelinde yapılandırma kullandığınızda her projenin dahil edilip edilmeyeceğini belirten onay kutularını da seçebilirsiniz.

İstediğiniz konfigürasyonları ayarladıktan sonra, bu yapılandırmalara uygun proje özelliklerini ayarlayabilirsiniz.

### <a name="set-properties-based-on-configurations"></a>Yapılandırma tabanlı özellikleri ayarla

Yapılandırma tabanlı özellikleri ayarlamak için, **Çözüm Gezgini**' de bir proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin. Yapılandırmalarınızın özelliklerini ayarlayabilirsiniz. Örneğin, bir yayın yapılandırması için, çözüm oluşturulduğunda kodun iyileştirildiği ve hata ayıklama yapılandırmasında `DEBUG` koşullu derleme sembolünün dahil edileceğini belirtebilirsiniz.

Özellik sayfası ayarları hakkında daha fazla bilgi için bkz. [Proje ve çözüm özelliklerini yönetme](../ide/managing-project-and-solution-properties.md).

## <a name="create-a-project-configuration"></a>Proje yapılandırması oluşturma

1. **Configuration Manager** iletişim kutusunu açın.

2. **Proje** sütununda bir proje seçin.

3. Bu projenin **yapılandırma** açılan listesinde, **Yeni**' yi seçin.

     **Yeni proje yapılandırması** iletişim kutusu açılır.

4. **Ad** kutusuna yeni yapılandırma için bir ad girin.

5. Varolan bir proje yapılandırmasından özellik ayarlarını kullanmak için, ayarları aşağı açılan listeden **Kopyala** listesinden bir yapılandırma seçin.

6. Aynı zamanda çözüm genelinde bir yapılandırma oluşturmak için **yeni çözüm yapılandırması oluştur** onay kutusunu seçin.

## <a name="rename-a-project-configuration"></a>Proje yapılandırmasını yeniden adlandırma

1. **Configuration Manager** iletişim kutusunu açın.

2. **Proje** sütununda, yeniden adlandırmak istediğiniz proje yapılandırmasına sahip projeyi seçin.

3. Bu projenin **yapılandırma** açılan listesinde **Düzenle**' yi seçin.

     **Proje yapılandırmasını düzenle** iletişim kutusu açılır.

4. Değiştirmek istediğiniz proje yapılandırma adını seçin.

5. **Yeniden Adlandır**' ı seçin ve ardından yeni bir ad girin.

## <a name="create-and-modify-solution-wide-build-configurations"></a>Çözüm genelinde derleme yapılandırması oluşturma ve değiştirme

### <a name="to-create-a-solution-wide-build-configuration"></a>Çözüm genelinde derleme yapılandırması oluşturmak için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Etkin çözüm yapılandırması** açılan listesinde, **Yeni**' yi seçin.

     **Yeni çözüm yapılandırması** iletişim kutusu açılır.

3. **Ad** metin kutusuna yeni yapılandırma için bir ad girin.

4. Ayarları varolan bir çözüm yapılandırmasından kullanmak için, ayarları açılan listeden **Kopyala** listesinden bir yapılandırma seçin.

5. Aynı anda proje yapılandırması oluşturmak istiyorsanız **Yeni proje yapılandırması oluştur** onay kutusunu seçin.

### <a name="to-rename-a-solution-wide-build-configuration"></a>Çözüm genelinde bir yapı yapılandırmasını yeniden adlandırmak için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Etkin çözüm yapılandırması** açılan listesinde, **Düzenle**' yi seçin.

     **Çözüm yapılandırmasını düzenle** iletişim kutusu açılır.

3. Değiştirmek istediğiniz çözüm yapılandırma adını seçin.

4. **Yeniden Adlandır**' ı seçin ve ardından yeni bir ad girin.

### <a name="to-modify-a-solution-wide-build-configuration"></a>Çözüm genelinde bir yapı yapılandırmasını değiştirmek için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Etkin çözüm yapılandırması** açılan listesinde, istediğiniz yapılandırmayı seçin.

3. **Proje bağlamları** bölmesinde her proje Için istediğiniz **yapılandırma** ve **platformu** seçin **ve oluşturulup oluşturulmayacağını** ve **dağıtıp dağıtamayacağını** seçin.

## <a name="see-also"></a>Ayrıca bkz.

- [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md)
- [Visual Studio 'da projeler ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md)
- [Proje ve çözüm özelliklerini yönetme](managing-project-and-solution-properties.md)
- [Yapılandırma oluşturma ve düzenleme (Mac için Visual Studio)](/visualstudio/mac/create-and-edit-configurations)

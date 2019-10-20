---
title: 'Nasıl yapılır: yapılandırma oluşturma ve düzenleme | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
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
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d5f5d8bb92b80942a95528a0b2e4c7e64bbfafc8
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72668137"
---
# <a name="how-to-create-and-edit-configurations"></a>Nasıl Yapılır: Yapılandırmaları Oluşturma ve Düzenleme
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Bir çözüm için birkaç yapı yapılandırması oluşturabilirsiniz. Örneğin, sınayıcılarınızın sorunları bulmak ve gidermek için kullanabileceği bir hata ayıklama derlemesi yapılandırabilir ve farklı müşterilere dağıtabileceğiniz farklı tür yapılar yapılandırabilirsiniz.

 [!INCLUDE[note_settings_general](../includes/note-settings-general-md.md)]

## <a name="creating-build-configurations"></a>Derleme yapılandırması oluşturma
 **Configuration Manager** iletişim kutusunu mevcut yapı yapılandırmalarının arasından seçim yapmak veya değiştirmek ya da yeni bir tane oluşturmak için kullanabilirsiniz.

#### <a name="to-open-the-configuration-manager-dialog-box"></a>Configuration Manager iletişim kutusunu açmak için

- **Çözüm Gezgini**, çözüm için kısayol menüsünü açın ve **Configuration Manager**öğesini seçin.

  > [!NOTE]
  > **Configuration Manager** komutu kısayol menüsünde görünmezse, menü çubuğunda **derleme** menüsünün altına bakın. Burada görünmezse, menü çubuğunda **Araçlar**, **Seçenekler**' i seçin ve ardından **Seçenekler** iletişim kutusunun sol bölmesinde, **Projeler ve çözümler**, **genel**' i genişletin ve sağ bölmedeki göster ' i seçin.  **Gelişmiş derleme yapılandırması** onay kutusu.

   **Configuration Manager** iletişim kutusunda, çözüm genelinde bir yapı yapılandırması seçmek, var olan bir yapılandırmayı değiştirmek veya yeni bir yapılandırma oluşturmak için **etkin çözüm yapılandırma** açılan listesini kullanabilirsiniz. **Etkin çözüm platformu** açılan listesini, yapılandırmanın hedeflediği platformu seçmek, var olan bir nesneyi değiştirmek veya yeni bir platform eklemek için kullanabilirsiniz. **Proje bağlamları** bölmesinde, çözümdeki projeler listelenir. Her proje için, projeye özgü bir yapılandırma ve platform seçebilir, var olanları değiştirebilir veya yeni bir yapılandırma oluşturabilir ya da yeni bir platform ekleyebilirsiniz. Çözümü derlemek veya dağıtmak için çözüm genelinde yapılandırma kullandığınızda her projenin dahil edilip edilmeyeceğini belirten onay kutularını da seçebilirsiniz.

  İstediğiniz konfigürasyonları ayarladıktan sonra, bu yapılandırmalara uygun proje özelliklerini ayarlayabilirsiniz.

#### <a name="to-set-properties-based-on-configurations"></a>Yapılandırma tabanlı özellikleri ayarlamak için

- **Çözüm Gezgini**, bir proje için kısayol menüsünü açın ve ardından **Özellikler**' i seçin.

     **Özellik sayfaları** penceresi açılır.

     Yapılandırmalarınızın özelliklerini ayarlayabilirsiniz. Örneğin, bir yayın yapılandırması için, çözüm oluşturulduğunda kodun iyileştirildiğini belirtebilir ve bir hata ayıklama yapılandırması için `DEBUG` koşullu derleme sembolünün dahil edileceğini belirtebilirsiniz. Özellik sayfası ayarları hakkında daha fazla bilgi için bkz. [Proje tasarımcısına giriş](https://msdn.microsoft.com/898dd854-c98d-430c-ba1b-a913ce3c73d7).

## <a name="creating-and-modifying-project-configurations"></a>Proje yapılandırması oluşturma ve değiştirme

#### <a name="to-create-a-project-configuration"></a>Proje yapılandırması oluşturmak için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Proje** sütununda bir proje seçin.

3. Bu projenin **yapılandırma** açılan listesinde, **Yeni**' yi seçin.

     **Yeni proje yapılandırması** iletişim kutusu açılır.

4. **Ad** kutusuna yeni yapılandırma için bir ad girin.

5. Varolan bir proje yapılandırmasından özellik ayarlarını kullanmak için, ayarları aşağı açılan listeden **Kopyala** listesinden bir yapılandırma seçin.

6. Aynı zamanda çözüm genelinde bir yapılandırma oluşturmak için **yeni çözüm yapılandırması oluştur** onay kutusunu seçin.

#### <a name="to-rename-a-project-configuration"></a>Proje yapılandırmasını yeniden adlandırmak için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Proje** sütununda, yeniden adlandırmak istediğiniz proje yapılandırmasına sahip projeyi seçin.

3. Bu projenin **yapılandırma** açılan listesinde **Düzenle**' yi seçin.

     **Proje yapılandırmasını düzenle** iletişim kutusu açılır.

4. Değiştirmek istediğiniz proje yapılandırma adını seçin.

5. **Yeniden Adlandır**' ı seçin ve ardından yeni bir ad girin.

## <a name="creating-and-modifying-solution-wide-build-configurations"></a>Çözüm genelinde derleme yapılandırması oluşturma ve değiştirme

#### <a name="to-create-a-solution-wide-build-configuration"></a>Çözüm genelinde derleme yapılandırması oluşturmak için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Etkin çözüm yapılandırması** açılan listesinde, **Yeni**' yi seçin.

     **Yeni çözüm yapılandırması** iletişim kutusu açılır.

3. **Ad** metin kutusuna yeni yapılandırma için bir ad girin.

4. Ayarları varolan bir çözüm yapılandırmasından kullanmak için, ayarları açılan listeden **Kopyala** listesinden bir yapılandırma seçin.

5. Aynı anda proje yapılandırması oluşturmak istiyorsanız **Yeni proje yapılandırması oluştur** onay kutusunu seçin.

#### <a name="to-rename-a-solution-wide-build-configuration"></a>Çözüm genelinde bir yapı yapılandırmasını yeniden adlandırmak için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Etkin çözüm yapılandırması** açılan listesinde, **Düzenle**' yi seçin.

     **Çözüm yapılandırmasını düzenle** iletişim kutusu açılır.

3. Değiştirmek istediğiniz çözüm yapılandırma adını seçin.

4. **Yeniden Adlandır**' ı seçin ve ardından yeni bir ad girin.

#### <a name="to-modify-a-solution-wide-build-configuration"></a>Çözüm genelinde bir yapı yapılandırmasını değiştirmek için

1. **Configuration Manager** iletişim kutusunu açın.

2. **Etkin çözüm yapılandırması** açılan listesinde, istediğiniz yapılandırmayı seçin.

3. **Proje bağlamları** bölmesinde her proje Için istediğiniz **yapılandırma** ve **platformu** seçin **ve oluşturulup oluşturulmayacağını** ve **dağıtıp dağıtamayacağını** seçin.

## <a name="see-also"></a>Ayrıca Bkz.
 [Derleme yapılandırmalarını anlama](../ide/understanding-build-configurations.md) [Visual Studio 'Da proje ve çözümler oluşturma ve Temizleme](../ide/building-and-cleaning-projects-and-solutions-in-visual-studio.md) [: proje özelliklerini ve yapılandırma ayarlarını değiştirme](https://msdn.microsoft.com/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)

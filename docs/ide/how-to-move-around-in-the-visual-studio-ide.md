---
title: IDE 'de gezinme
description: Visual Studio ıde 'nin içinden pencereye ve dosya dosyasını birkaç farklı şekilde dosyaya taşımayı öğrenin.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
helpviewer_keywords:
- environments [Visual Studio], navigation
- documents [Visual Studio], navigating
- IDE, navigation
- navigation [Visual Studio]
- files [Visual Studio], navigating between
- windows [Visual Studio], navigating
- Window.NextDocumentWindowNav
- IDE navigator
ms.assetid: 6c36b6eb-c93f-496b-af08-4199f7afd8bd
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.technology: vs-ide-general
ms.workload:
- multiple
ms.openlocfilehash: 8f3f41dfb6c1f53175d163ece81ed66fd9cc10d8
ms.sourcegitcommit: 68897da7d74c31ae1ebf5d47c7b5ddc9b108265b
ms.translationtype: MT
ms.contentlocale: tr-TR
ms.lasthandoff: 08/13/2021
ms.locfileid: "122137398"
---
# <a name="how-to-move-around-in-the-visual-studio-ide"></a>nasıl yapılır: Visual Studio ıde 'de gezinme

Tümleşik geliştirme ortamı (IDE), tercihlerinize veya proje gereksinimlerinize bağlı olarak, pencereden pencereye ve dosyaya farklı yollarla dosya taşımanıza olanak tanımak üzere tasarlanmıştır. Düzenleyicideki açık dosyalar arasında dolaşmayı veya IDE 'deki tüm etkin araç pencerelerini kullanarak geçiş yapabilirsiniz. Ayrıca, son erişildiği sırada ne olursa olsun, düzenleyicide açık olan herhangi bir dosyaya doğrudan geçiş yapabilirsiniz. Bu özellikler, IDE 'de çalışırken üretkenliğinizi artırmaya yardımcı olabilir.

> [!NOTE]
> İletişim kutularında kullanılabilen seçenekler ve gördüğünüz menü komutlarının adları ve konumları, etkin ayarlarınıza veya sürümüne bağlı olarak bu makalede açıklananlar arasından farklılık gösterebilir. Bu makale, **genel** ayarlar göz önünde bulundurularak yazılmıştır. ayarlarınızı değiştirmek (örneğin, **genel** veya **Visual C++** ayarları) için **araçlar**  >  **içeri aktar ve dışarı aktar Ayarlar**' ı seçin ve ardından **tüm ayarları sıfırla**' yı seçin.

## <a name="keyboard-shortcuts"></a>Klavye kısayolları

Visual Studio neredeyse her menü komutunda klavye kısayolu bulunur. Kendi özel kısayollarınızı da oluşturabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

## <a name="navigate-among-files-in-the-editor"></a>Düzenleyicideki dosyalar arasında gezinme

Düzenleyicide açık olan dosyalar arasında gezinmek için çeşitli yöntemler kullanabilirsiniz. Dosyalara erişmek istediğiniz sıraya göre dosyalar arasında geçiş yapabilirsiniz, daha önce açık olan herhangi bir dosyayı hızlı bir şekilde bulmak için IDE gezginini kullanın veya her zaman görünür olmaları için sık kullanılan dosyaları sekmeye uygun olarak sabitleyin.

Geriye doğru ilerleyin ve Microsoft Internet Explorer 'da görüntüleme geçmişiniz için, geri ve ileri ' ye benzer şekilde, düzenleyicide bulunan açık dosyalar üzerinden ileri döngülerine gidin.

### <a name="to-move-through-open-files-in-order-of-use"></a>Açık dosyalar aracılığıyla kullanım sırasıyla geçiş yapmak için

- Açık belgeleri en son dokundukları sırada etkinleştirmek için **CTRL** + **-** (kısa çizgi) tuşuna basın.

- Açık belgeleri ters sırada etkinleştirmek için **CTRL** + **SHIFT** + **-** (kısa çizgi) tuşuna basın.

    > [!NOTE]
    > **Geriye giderek** **İleri** git **Görünüm** menüsünde de bulunabilir.

ayrıca, dosyaya son erişiminizden bağımsız olarak, **ıde gezginini**, düzenleyicideki **etkin dosyalar** listesini veya **Windows** iletişim kutusunu kullanarak, düzenleyicide açık olan belirli bir dosyaya geçiş yapabilirsiniz.

**ıde gezgini** Windows uygulama değiştiricisinden çok benzer şekilde çalışmaktadır. Menülerden kullanılamaz ve yalnızca kısayol tuşları kullanılarak erişilebilir. **IDE Gezginine** erişmek için iki komuttan birini kullanabilirsiniz (aşağıda gösterildiği gibi), üzerinde geçiş yapmak istediğiniz sıraya bağlı olarak dosyalar arasında geçiş yapmak için iki komuttan yararlanabilirsiniz.

![Visual Studio IDE Gezgini](../ide/media/vs2015_ide_navigator.png)

`Window.PreviousDocumentWindowNav` en son erişilen dosyaya taşımanızı sağlar ve `Window.NextDocumentWindowNav` ters sırada taşımanızı sağlar. **genel geliştirme Ayarlar** **shıft** + **alt** + **f7** 'e `Window.PreviousDocumentWindowNav` ve **alt** + **f7** `Window.NextDocumentWindowNav` 'e atar.

> [!NOTE]
> Kullandığınız ayarlar birleşimine bu komuta atanmış kısayol tuşu birleşimi zaten yoksa, **Seçenekler** Iletişim kutusunun **klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-specific-files-in-the-editor"></a>Düzenleyicideki belirli dosyalara geçiş yapmak için

-  +  **IDE Gezginini** göstermek için CTRL tuşuna basın. **CTRL** tuşunu basılı tutun ve geçiş yapmak istediğiniz dosyayı seçene kadar **sekme** tuşuna basın.

    > [!TIP]
    > **Etkin dosyalar** listesinden gittiğiniz sırayı tersine çevirmek için **CTRL** + **SHIFT** tuşlarını basılı tutarak **Tab** tuşuna basın.

    \- veya

- Düzenleyicinin sağ üst köşesinde **etkin dosyalar** düğmesini seçin ve ardından listeden bir dosyayı seçerek geçiş yapın.

    \- veya

- menü çubuğunda, **pencere**  >  **Windows**' yi seçin.

- Listede, görüntülemek istediğiniz dosyayı seçin ve ardından **Etkinleştir**' i seçin.

## <a name="navigate-among-tool-windows-in-the-ide"></a>IDE 'deki araç pencereleri arasında gezinme

**IDE Gezgini** , IDE 'de açtığınız araç pencereleri arasında geçiş yapmanızı de sağlar. **IDE Gezginine** erişmek için iki komuttan birini kullanarak, geçiş yapmak istediğiniz sıraya bağlı olarak araç pencereleri arasında geçiş yapabilirsiniz. `Window.PreviousToolWindowNav` en son erişilen dosyaya taşımanızı sağlar ve `Window.NextToolWindowNav` ters sırada taşımanızı sağlar. **genel geliştirme Ayarlar** **shıft** + **alt** + **f7** 'e `Window.PreviousDocumentWindowNav` ve **alt** + **f7** `Window.NextDocumentWindowNav` 'e atar.

> [!NOTE]
> Kullandığınız ayarlar birleşimine bu komuta atanmış kısayol tuşu birleşimi zaten yoksa, **Seçenekler** Iletişim kutusunun **klavye** sayfasını kullanarak kendi özel komutunuzu atayabilirsiniz. Daha fazla bilgi için bkz. [klavye kısayollarını tanımlamak ve özelleştirmek](../ide/identifying-and-customizing-keyboard-shortcuts-in-visual-studio.md).

### <a name="to-switch-to-a-specific-tool-window-in-the-ide"></a>IDE 'de belirli bir araç penceresine geçiş yapmak için

-  + **IDE Gezginini** göstermek için alt **F7** tuşuna basın. Geçiş yapmak istediğiniz pencereyi seçene kadar **alt** tuşunu basılı tutun ve **F7** tuşuna basın.

    > [!TIP]
    > **etkin araç Windows** listesinden gittiğiniz sırayı tersine çevirmek için **shıft** + **Alt** tuşlarını basılı tutun ve **F7** tuşuna basın.

## <a name="see-also"></a>Ayrıca bkz.

- [Pencere düzenlerini özelleştirme](../ide/customizing-window-layouts-in-visual-studio.md)
- [Varsayılan klavye kısayolları](../ide/default-keyboard-shortcuts-in-visual-studio.md)
